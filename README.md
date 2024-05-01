# Project-Cost-Optimization-EBS

AWS Cloud Project.

![image](https://github.com/RitikPyCode/Project-Cost-Optimization-EBS/assets/69500530/5ab8d27c-c76e-4b81-a05d-388f05f1c35b)



## AWS Cloud Cost Optimization - Identifying Stale Resources

### Identifying Stale EBS Snapshots

In this example, we'll create a Lambda function that identifies EBS snapshots that are no longer associated with any active EC2 instance and deletes them to save on storage costs.

#### Description:
The Lambda function fetches all EBS snapshots owned by the same account ('self') and also retrieves a list of active EC2 instances (running and stopped). For each snapshot, it checks if the associated volume (if exists) is not associated with any active instance. If it finds a stale snapshot, it deletes it, effectively optimizing storage costs.


STEPS:
-----------

#### Create EC2 Instance and Volume:
Launch a new EC2 instance from the AWS Management Console.
Attach a volume to the instance during or after creation.

#### Create Snapshot:
Generate a snapshot of the volume associated with the EC2 instance.

#### Create Lambda Function:
Navigate to the Lambda service on the AWS Management Console.
Create a new Lambda function with default settings.
Paste the provided Python code into the Lambda function editor.

#### Deploy and Test:
Deploy the Lambda function.
Save the changes by pressing Ctrl+S.
Test the Lambda function by clicking on "Test project".

##### You may encounter an error message stating: "DescribeSnapshots operation: You are not authorized to perform this operation."

#### Note: Default execution time in lambda is 03 seconds. (go in configuration section)

##### ++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

In the Configuration section, adjust the default execution time from 03 seconds to 10 seconds.
Go to configuration> permissions > click on role name
Go to IAM tab> 
We will give or attach policy
Describe the snapshot
Delete the snapshot

### SUMMARY OF ABOVE STEPS: 

"Navigate to the Configuration tab, then click on Permissions, followed by the role name. Next, access the IAM tab where you will assign or attach the necessary policy for describing and deleting snapshots. If you cannot locate the snapshot permission, create your own policy by selecting "Create policy inline". Choose EC2 as the action and specify allowed actions (DescribeSnapshot, DeleteSnapshot) with resources set to All. After creating the policy, test it in Lambda once more. If you encounter another error regarding describing instances, you will need to address it accordingly."

### (DescribeSnapshot, DeleteSnapshot)

##### ++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

Steps: if you are not able to find the snapshot permission so please create your own policy.
Create policy inline> in action choose ec2> allowed action (describesnapshot, deletesnapshot)> resources All > next.
Test it in lambda again.
Again we will get an error to describe instance 
Again go to attach policy inline and choose ec2> drop down list> choose describeinstances & describevolumns
After doing all these things.
Go to lambada and test the code.
Now you will see, successful executed.
You can see snapshot still there. If you are deleting the intance but still snapshot will be there. becuase u have to ask with your team can we deleted this snapshot as well If snapshot is 30 days old then please delete it.
First deleted instance > then re-run the code click on test.
stale snapshot means, it's no longer needed and taking much storage which is nt required.

##### ++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

### SUMMARY OF ABOVE STEPS: 
" Once more, attach a policy inline and select EC2 from the dropdown list. Choose "DescribeInstances" and "DescribeVolumes" actions. After completing these steps, return to Lambda and test the code. You should observe successful execution. Note that the snapshot will still persist even after deleting the instance. Discuss with your team the possibility of implementing a policy to automatically delete snapshots that are older than 30 days. After deleting the instance, rerun the code and test it again. Remember, stale snapshots consume unnecessary storage and should be removed to optimize resources."

#### "DescribeInstances" and "DescribeVolumes"


#### Img: 1

![specify permissions](https://github.com/RitikPyCode/Project-Cost-Optimization-EBS/assets/69500530/0b726757-6c97-4e22-a183-585bbbd056c0)


#### Img: 2


![specify permissions2](https://github.com/RitikPyCode/Project-Cost-Optimization-EBS/assets/69500530/c4fc75c2-13fb-488f-ad9d-b7a0ccbd87e8)


#### Img: 3


![review and save](https://github.com/RitikPyCode/Project-Cost-Optimization-EBS/assets/69500530/1f461e9b-22df-4699-9206-fa42eeae0f1e)


#### Img: 4


![Lambda test](https://github.com/RitikPyCode/Project-Cost-Optimization-EBS/assets/69500530/3e6b150a-6ac6-4039-9b5d-1a2b3dc7a07a)


#### Img: 5


![got executed sussfully](https://github.com/RitikPyCode/Project-Cost-Optimization-EBS/assets/69500530/721878b0-63cf-41f3-938b-c6f4f76eab8a)


#### Img: 6


![after delete the instnce](https://github.com/RitikPyCode/Project-Cost-Optimization-EBS/assets/69500530/a839b533-7f3b-4223-ab8a-79ec8a2f051a)


#### Img: 7


![deleted snapshot](https://github.com/RitikPyCode/Project-Cost-Optimization-EBS/assets/69500530/c28e5b9e-93ee-40e6-8b6d-08ee50e3e50f)


#### Img: 8


![alll 0](https://github.com/RitikPyCode/Project-Cost-Optimization-EBS/assets/69500530/934afb01-3607-42e7-b266-94b3e65c235f)




###### By following these steps, you can optimize costs in AWS Cloud by efficiently managing snapshots and ensuring that unnecessary resources are removed, reducing storage costs and improving resource utilization.



#### FOLLOW FOR MORE: https://www.linkedin.com/in/ritikktiwari/


++++++++++++++++++++++++++++++++++++++++++++++

##### CREDIT GOEAS TO @ABHISHEK VIRRAMALLA
##### EDITED AND CREATED BY @RITIK KUMAR TIWARI
##### LAB PERFORMED BY @RITIK KUMAR TIWARI

++++++++++++++++++++++++++++++++++++++++++++++
THNAK YOU!! 
