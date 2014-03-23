template: lucid.haml
title: Contact details
---
---
##Appendix (sample code)
###Sample code for creating a signature
You'll need to pass along a signature and a developer ID &ndash; or "devid" &ndash; with every request using HTTP GET. 
The signature value is a HMAC-SHA1 hash of the completed request (minus the base URL but including your developer ID, known as "devid") and the key.
###Example in .net C#
The following is the .net C#  code snippet for the signature calculation.<a href="#fig-example-csharp"></a>
<div id="fig-example-csharp">
    <h4>C# sample code</h4>
Note: key values are used for example purposes only.


<pre>
string key = "9c132d31-6a30-4cac-8d8b-8a1970834799"; // supplied by PTV
int developerId = 2; // supplied by PTV
string url = "/v2/mode/2/line/787/stops-for-line"; // the PTV api method we want


// add developer id
url = string.Format("{0}{1}devid={2}",url,url.Contains("?") ? "&" : "?",developerId);
System.Text.ASCIIEncoding encoding = new System.Text.ASCIIEncoding();
// encode key
byte[] keyBytes = encoding.GetBytes(key);
// encode url
byte[] urlBytes = encoding.GetBytes(url);
byte[] tokenBytes = new System.Security.Cryptography.HMACSHA1(keyBytes).ComputeHash(urlBytes);
var sb = new System.Text.StringBuilder();
// convert signature to string
Array.ForEach<byte>(tokenBytes, x => sb.Append (x.ToString("X2")));
// add signature to url
url = string.Format("{0}&signature={1}",url,sb.ToString());


// extra code to add base URL &ndash; the resultant url should be:
//  http://timetableapi.ptv.vic.gov.au/v2/mode/2/line/787/stops-for-line?devid=2&signature=D5474F344CDAA7B92F2253169F6C1D66C1A15001
</pre>
</div>




###Example in Java
The following is the Java code snippet for the signature calculation.
Note: key values are used for example purposes only.<a href="#fig-example-java"></a>
<div id="fig-example-java">
<h4>Java sample code</h4>
<pre>

    /**
     * Generates a signature using the HMAC-SHA1 algorithm 
     * 
     * @param privateKey - Developer Key supplied by PTV
     * @param uri - request uri (Example :/v2/HealthCheck) 
     * @param developerId - Developer ID supplied by PTV
     * @return Unique Signature Value  
     */
    public String generateSignature(final String privateKey, final String uri, final int developerId)
    {
        String encoding = "UTF-8";
        String HMAC_SHA1_ALGORITHM = "HmacSHA1";
        String signature;
        StringBuffer uriWithDeveloperID = new StringBuffer();
        uriWithDeveloperID.append(uri).append(uri.contains("?") ? "&" : "?").append("devid="+developerId);     
        try
        {
            byte[] keyBytes = privateKey.getBytes(encoding);
            byte[] uriBytes = uriWithDeveloperID.toString().getBytes(encoding);
            Key signingKey = new SecretKeySpec(keyBytes, HMAC_SHA1_ALGORITHM);
            Mac mac = Mac.getInstance(HMAC_SHA1_ALGORITHM);
            mac.init(signingKey);
            byte[] signatureBytes = mac.doFinal(uriBytes);
            StringBuffer buf = new StringBuffer(signatureBytes.length * 2);
            for (byte signatureByte : signatureBytes)
            {
                int intVal = signatureByte & 0xff;
                if (intVal < 0x10)
                {
                    buf.append("0");
                }
                buf.append(Integer.toHexString(intVal));
            }
            signature = buf.toString();
        }
        catch (UnsupportedEncodingException e)
        {
            throw new RuntimeException(e);
        }
        catch (NoSuchAlgorithmException e)
        {
            throw new RuntimeException(e);
        }
        catch (InvalidKeyException e)
        {
            throw new RuntimeException(e);
        }
        return signature.toString().toUpperCase();
    }
    
    /**
     * Generate full URL using generateSignature() method
     * 
     * @param privateKey - Developer Key supplied by PTV (Example :  "92dknhh31-6a30-4cac-8d8b-8a1970834799");
     * @param uri - request uri (Example :"/v2/mode/2/line/787/stops-for-line) 
     * @param developerId - Developer ID supplied by PTV( int developerId )
     * @return - Full URL with Signature
     */
    public String generateCompleteURLWithSignature(final String privateKey, final String uri, final int developerId)
    {
        
        String baseURL="http://timetableapi.ptv.vic.gov.au";
        StringBuffer url = new StringBuffer(baseURL).append(uri).append(uri.contains("?") ? "&" : "?").append("devid="+developerId).append("&signature="+generateSignature(privateKey, uri, developerId));
        return url.toString();
      
    }

</pre>
</div>


###Example in Objective C
The following is the Objective C code snippet for the signature calculation.
Note: key values are used for example purposes only. <a href="#fig-example-objectivec"></a>
<div id="fig-example-objectivec">
<h4>Objective C sample code</h4>
<pre>
-(NSURL*) generateURLWithDevIDAndKey:(NSString*)urlPath {
    
    NSString *hardcodedURL = @" http://timetableapi.ptv.vic.gov.au";
    NSString *hardcodedDevID = @"developerID provided by PTV";
    NSString *hardcodedkey = @"developer key provided by PTV";
    
/*    urlPath = @" http://timetableapi.ptv.vic.gov.au/v2/mode/2/line/787/stops-for-line";
*/
    NSRange deleteRange ={0,[hardcodedURL length]};
    NSMutableString *urlString = [[NSMutableString alloc]initWithString:urlPath];
    [urlString deleteCharactersInRange:deleteRange];
    if( [urlString containsString:@"?"])
        [urlString appendString:@"&"];
    else
        [urlString appendString:@"?"];
    
    [urlString appendFormat:@"devid=%@",hardcodedDevID];
    
    
    const char *cKey  = [hardcodedkey cStringUsingEncoding:NSUTF8StringEncoding];
    const char *cData = [urlString cStringUsingEncoding:NSUTF8StringEncoding];
    unsigned char cHMAC[CC_SHA1_DIGEST_LENGTH];
    CCHmac(kCCHmacAlgSHA1, cKey, strlen(cKey), cData, strlen(cData), cHMAC);
    
    NSString *hash;
    
    NSMutableString* output = [NSMutableString stringWithCapacity:CC_SHA1_DIGEST_LENGTH * 2];
    
    for(int i = 0; i < CC_SHA1_DIGEST_LENGTH; i++)
        [output appendFormat:@"%02x", cHMAC[i]];
    hash = output;
    
    NSString* signature = [hash uppercaseString];
    NSString *urlSuffix = [NSString stringWithFormat:@"devid=%@&signature=%@", hardcodedDevID,signature];
    
    NSURL *url = [NSURL URLWithString:urlPath];
    NSString *urlQuery = [url query];
    if(urlQuery != nil && [urlQuery length] > 0){
        url = [NSURL URLWithString:[NSString stringWithFormat:@"%@&%@",urlPath,urlSuffix]];
    }else{
        url = [NSURL URLWithString:[NSString stringWithFormat:@"%@?%@",urlPath,urlSuffix]];
    }
    
    return url;
}
</pre>
</div>