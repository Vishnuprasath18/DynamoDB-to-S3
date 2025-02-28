# DynamoDB-to-S3
**Step by step Breakdown:**
**Step 1: Set up the S3 bucket**  
- Go to the S3 console → Create bucket → Name it `dynamodb-csv-export-bucket` (or any unique name)  
- Leave all settings default → Create bucket  

**Step 2: Create the DynamoDB table**  
- Go to DynamoDB console → Create table  
- Table name: `UserData`  
- Partition key: `id` (String)  
- Add some sample data:  
```json
{
  "id": "1",
  "name": "Alice",
  "email": "alice@example.com"
}
```

**Step 3: Create the Lambda function**  
- Go to the Lambda console → Create function  
- Name: `DynamoDBToCSV`  
- Runtime: Python 3.12  
- Role: Create a new role with basic permissions  

**Step 4: Add permissions to the Lambda role**  
- Go to IAM → Roles → Find your Lambda role  
- Attach policies:  
  - **AmazonDynamoDBReadOnlyAccess**  
  - **AmazonS3FullAccess**  

**Step 5: Write the Lambda function**  
Replace the default code with this:  
```
  lambda_func.py
```

**Step 6: Test the function**  
- In Lambda, click "Test" → Create a new test event (empty payload)  
- Click "Test" again — you should see a success message  
- Go to your S3 bucket → Check for the `dynamodb_data.csv` file 🎉  

**Step 7: (Optional) Trigger from DynamoDB events**  
If you want the CSV to be updated every time data changes:  
- Go to DynamoDB → Streams → Enable stream on the table  
- Add a trigger in Lambda → Choose the DynamoDB stream  
 
