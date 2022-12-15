# Camunda/Robocorp examples
The following are few examples of  workflows used in formsflow.
## Table of Contents
1. [Notification Email](#notification-email)
2. [One step Approval](#one-step-approval)
3. [Two step Approval](#two-step-approval)
4. [Background Check Robot](#background-check-robot)
# Notification Email
This bpmn diagram is intended to send an email notification to respective users. It uses **email-template.dmn** to configure the email properties.
## Type
BPMN
## How it Works

![image](https://user-images.githubusercontent.com/96716528/207521941-fee5fa71-6f71-4bc6-9816-d0e2e04ebff3.png)

First, configure notify listener to the desired workflow step. This will invoke the notify listener and start the message event of email-notification bpmn.


![image](https://user-images.githubusercontent.com/96716528/207522000-579bec45-2488-4da5-ab6b-45621af5c5fe.png)



The notification_email workflow connects with the email-template-example.dmn with the decision reference value **email-template-example**.


![image](https://user-images.githubusercontent.com/96716528/207522072-497fa80a-8cf5-4318-ac5f-f51d270acbb0.png)


 EmailAttributesListener is configured between the email template and email connector, which takes output data from the dmn template and transfers it to the email connector to send the mail.
 

![image](https://user-images.githubusercontent.com/96716528/207522113-aabc1c5b-822e-42b2-ae6b-c261fbcafe7c.png)



# One step Approval
## Type
BPMN
## How it Works

![image](https://user-images.githubusercontent.com/96716528/207522495-ef0fd2e5-288d-41d4-89e6-df134e8ad6c7.png)

This diagram shows a simple approval process. Submit a form to invoke the process.


Add below listeners to inject the fields, capture the audit and transform camunda variables.

- org.camunda.bpm.extension.hooks.listeners.BPMFormDataPipelineListener

- org.camunda.bpm.extension.hooks.listeners.ApplicationStateListener

- org.camunda.bpm.extension.hooks.listeners.FormBPMFilteredDataPipelineListener

After that exclusive gateway checks the condition and decides to approve/ reject the application

# Two step Approval
This bpmn diagram can be used for any state of approval process.
## Type
BPMN
## How it Works
![image](https://user-images.githubusercontent.com/96716528/207524812-4c320a7d-5c6f-4409-bd10-4953dc19484a.png)

This is a two-step approval process that involves three lanes including the client and reviewers in the process.
After the client submits the form, the first step reviewer accepts/rejects the application with comments. If accepted, the application goes to the next step, and if rejected client needs to resubmit the form for approval.
After the first step,  the next level reviewer approves the application and the process is completed, if rejected, the client is notified to resubmit the form.

# Background Check Robot
Refer this [Background Check](https://github.com/AOT-Technologies/forms-flow-ai-extensions/blob/master/rpa-robocorp-extension/external-client-extension/starter-examples/robots/background-check-robot-readme.md) Robot and [Usage](https://github.com/AOT-Technologies/forms-flow-ai-extensions/blob/master/rpa-robocorp-extension/external-client-extension/USAGE.md). 
