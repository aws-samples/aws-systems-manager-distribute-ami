# Distribute an Amazon Machine Image to another AWS Account using AWS Application Migration Service Post-launch automation

Read the full blog post [Distribute an Amazon Machine Image to another AWS Account using AWS Application Migration Service Post-launch automation](https://aws.amazon.com/blogs/mt/distribute-an-amazon-machine-image-to-another-aws-account-using-aws-application-migration-service-post-launch-automation/) (yet to be published)

## Implementation

Use the following steps to create the Automation Document and configure the Application Migration Service to run the document as a post-launch custom action:

### Create Automation Document
1. On the AWS Systems Manager console, choose **Documents** in the navigation pane.
1. Choose **Create document** *Automation*.
1. Select the pencil icon and enter a **document name**.
1. Choose **Code** to move to code input screen.
1. Copy contents from [distributeami.yml](./distributeami.yml).
1. Choose **Create runbook**.

The Automation Document is visible in documents “Owned by me”. This document is only available to your AWS Account.

### Activate Post-launch custom action

Post-launch settings must first be activated on the [Post-launch template](https://docs.aws.amazon.com/mgn/latest/ug/post-launch-settings-editing.html) page.

1. On the Application Migration Service console, choose **Source Servers** in the navigation pane.
1. Choose the source server to configure with post-launch settings (Can also be configured as a [Post-launch settings template](https://docs.aws.amazon.com/mgn/latest/ug/post-launch-settings-editing.html) to be applied to all newly added servers).
1. Choose **Post-launch settings**.
1. Choose **Create action**.
1. Provide a name for the Action and ensure **Activate this action** is checked.
1. For *Systems Manager document name* choose the Automation Document you created.
1. Ensure the **Order** number is correct. It is likely AMI creation and sharing is the last post-launch action to be completed so it should have the **highest** order number.
1. Enter values for the **Action Parameters**. Some parameters are optional depending if copying the AMI into another AWS account is required.
1. Choose **Add action**. This step creates the action.

## Security

See [CONTRIBUTING](CONTRIBUTING.md#security-issue-notifications) for more information.

## License

This library is licensed under the MIT-0 License. See the LICENSE file.

