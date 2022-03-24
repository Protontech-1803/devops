# Customizing Oracle Cloud Advisor #
Oracle Cloud Advisor is used to find potential inefficiencies in a given tenancy and suggests a guided solution. From a customer point of view, it assists in Saving Money, Improving Performance, Strengthening System resilience and Improve security of the customers’ OCI tenancy.
In this POC, you will know how to start the Oracle Cloud Advisor and Customize. 
Prerequisites: The Prerequisite to start the Oracle Cloud Advisor on OCI, is to grant security access through a policy. For example, if the resource name for Cloud Advisor is optimizer-api-family, the below command grants the users access.

**Steps to Enable Oracle Cloud Advisor:**
Following are the steps to enable Oracle Cloud Advisor, if it is not enabled by default for a given tenancy in OCI.
1.	Login into the OCI Console, navigate through the side navigation menu and click **Governance & Administration** option. Under Cloud Advisor, click **Settings**. The Cloud Advisor Settings page opens.
 ![Alt text](https://github.com/Protontech-1803/devops/blob/master/CustomizingOracleCloudAdvisor/img/1.png)
2.	In the Cloud Advisor Setting page, Click **Activate Cloud Advisor**. The Activate Cloud Advisor dialog box pops up.
3.	In the Activate Cloud Advisor dialog box, click **Enable**.

**Customizing Oracle Cloud Advisor:**
Now, you will learn how to customize Oracle Cloud Advisor for a given tenancy in OCI. You can customize Cloud Advisor by postponing or dismissing recommendations and by customizing the logic that Cloud Advisor uses to make recommendations. Modify the recommendations based on your preferences and what works best for your workloads. Customizing Oracle Cloud Advisor is done by
1.	Customizing Overrides
2.	Customizing Recommendations for Specific Resources
3.	Customizing Recommendation for All Resources
In this POC, you will learn how to Customize Recommendations for Specific Resources.  For Example, consider to dismiss a recommendation for a specific resource.  The Following are the steps to dismiss recommendations so that the resource no longer appears on the recommendation list in Oracle Cloud Advisor.
1.	In the OCI Console, Open the navigation menu and click Governance & Administration. Under Cloud Advisor, click Recommendations. The Cloud Advisor Recommendations dashboard opens.
2.	Click the recommendation in the list to open the recommendation details panel. A list of individual resources with pending recommendations is displayed.
3.	Select the resources that you want to dismiss, and then click Dismiss selected.
4.	In the Dismiss recommendation panel, click Dismiss.
Similarly, Customizing Overrides and Customizing Recommendation for All Resources can be configured from OCI Console. Also, these customization can be carried out using CLI.



