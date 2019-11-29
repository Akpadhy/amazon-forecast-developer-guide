# CreateForecast<a name="API_CreateForecast"></a>

Creates a forecast for each item in the `TARGET_TIME_SERIES` dataset that was used to train the predictor\. This is known as inference\. To retrieve the forecast for a single item at low latency, use the [QueryForecast](API_forecastquery_QueryForecast.md) operation\. To export the complete forecast into your Amazon Simple Storage Service \(Amazon S3\) bucket, use the [CreateForecastExportJob](API_CreateForecastExportJob.md) operation\.

The range of the forecast is determined by the `ForecastHorizon` value, which you specify in the [CreatePredictor](API_CreatePredictor.md) request\. When you query a forecast, you can request a specific date range within the forecast\.

To get a list of all your forecasts, use the [ListForecasts](API_ListForecasts.md) operation\.

**Note**  
The forecasts generated by Amazon Forecast are in the same time zone as the dataset that was used to create the predictor\.

For more information, see [Forecasts](howitworks-forecast.md)\.

**Note**  
The `Status` of the forecast must be `ACTIVE` before you can query or export the forecast\. Use the [DescribeForecast](API_DescribeForecast.md) operation to get the status\.

## Request Syntax<a name="API_CreateForecast_RequestSyntax"></a>

```
{
   "[ForecastName](#forecast-CreateForecast-request-ForecastName)": "string",
   "[ForecastTypes](#forecast-CreateForecast-request-ForecastTypes)": [ "string" ],
   "[PredictorArn](#forecast-CreateForecast-request-PredictorArn)": "string"
}
```

## Request Parameters<a name="API_CreateForecast_RequestParameters"></a>

The request accepts the following data in JSON format\.

 ** [ForecastName](#API_CreateForecast_RequestSyntax) **   <a name="forecast-CreateForecast-request-ForecastName"></a>
A name for the forecast\.  
Type: String  
Length Constraints: Minimum length of 1\. Maximum length of 63\.  
Pattern: `^[a-zA-Z][a-zA-Z0-9_]*`   
Required: Yes

 ** [ForecastTypes](#API_CreateForecast_RequestSyntax) **   <a name="forecast-CreateForecast-request-ForecastTypes"></a>
The quantiles at which probabilistic forecasts are generated\. **You can currently specify up to 5 quantiles per forecast**\. Accepted values include `0.01 to 0.99` \(increments of \.01 only\) and `mean`\. The mean forecast is different from the median \(0\.50\) when the distribution is not symmetric \(for example, Beta and Negative Binomial\)\. The default value is `["0.1", "0.5", "0.9"]`\.  
Type: Array of strings  
Array Members: Minimum number of 1 item\. Maximum number of 20 items\.  
Pattern: `(^0?\.\d\d?$|^mean$)`   
Required: No

 ** [PredictorArn](#API_CreateForecast_RequestSyntax) **   <a name="forecast-CreateForecast-request-PredictorArn"></a>
The Amazon Resource Name \(ARN\) of the predictor to use to generate the forecast\.  
Type: String  
Length Constraints: Maximum length of 256\.  
Pattern: `^[a-zA-Z0-9\-\_\.\/\:]+$`   
Required: Yes

## Response Syntax<a name="API_CreateForecast_ResponseSyntax"></a>

```
{
   "[ForecastArn](#forecast-CreateForecast-response-ForecastArn)": "string"
}
```

## Response Elements<a name="API_CreateForecast_ResponseElements"></a>

If the action is successful, the service sends back an HTTP 200 response\.

The following data is returned in JSON format by the service\.

 ** [ForecastArn](#API_CreateForecast_ResponseSyntax) **   <a name="forecast-CreateForecast-response-ForecastArn"></a>
The Amazon Resource Name \(ARN\) of the forecast\.  
Type: String  
Length Constraints: Maximum length of 256\.  
Pattern: `^[a-zA-Z0-9\-\_\.\/\:]+$` 

## Errors<a name="API_CreateForecast_Errors"></a>

 **InvalidInputException**   
We can't process the request because it includes an invalid value or a value that exceeds the valid range\.  
HTTP Status Code: 400

 **LimitExceededException**   
The limit on the number of resources per account has been exceeded\.  
HTTP Status Code: 400

 **ResourceAlreadyExistsException**   
There is already a resource with this name\. Try again with a different name\.  
HTTP Status Code: 400

 **ResourceInUseException**   
The specified resource is in use\.  
HTTP Status Code: 400

 **ResourceNotFoundException**   
We can't find a resource with that Amazon Resource Name \(ARN\)\. Check the ARN and try again\.  
HTTP Status Code: 400

## See Also<a name="API_CreateForecast_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [AWS Command Line Interface](https://docs.aws.amazon.com/goto/aws-cli/forecast-2018-06-26/CreateForecast) 
+  [AWS SDK for \.NET](https://docs.aws.amazon.com/goto/DotNetSDKV3/forecast-2018-06-26/CreateForecast) 
+  [AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/forecast-2018-06-26/CreateForecast) 
+  [AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/forecast-2018-06-26/CreateForecast) 
+  [AWS SDK for Java](https://docs.aws.amazon.com/goto/SdkForJava/forecast-2018-06-26/CreateForecast) 
+  [AWS SDK for JavaScript](https://docs.aws.amazon.com/goto/AWSJavaScriptSDK/forecast-2018-06-26/CreateForecast) 
+  [AWS SDK for PHP V3](https://docs.aws.amazon.com/goto/SdkForPHPV3/forecast-2018-06-26/CreateForecast) 
+  [AWS SDK for Python](https://docs.aws.amazon.com/goto/boto3/forecast-2018-06-26/CreateForecast) 
+  [AWS SDK for Ruby V2](https://docs.aws.amazon.com/goto/SdkForRubyV2/forecast-2018-06-26/CreateForecast) 