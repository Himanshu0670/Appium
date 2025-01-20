# What is CucumberStudio
[CucumberStudio](https://support.smartbear.com/cucumberstudio/docs/index.html) is a collaborative testing platform in the cloud that allows the software delivery team to co-design acceptance tests. It provides a real-time environment for designing, executing and refactoring tests. Ultimately CucumberStudio enables to automate tests that become the living specification of your Apps.
CucumberStudio is intended to be used by everyone in a software delivery team: customers, domain experts, product managers, testers and developers.

## Prerequisites
- Download [Java](https://www.oracle.com/in/java/technologies/downloads/)
- Download [Eclipse](https://www.eclipse.org/downloads/)
- Download [Ruby](https://rubyinstaller.org/downloads/archives/) ,  there might be some compatibility issues in my case `2.6.0.1-x64`  works correctly.
- Set up an account on [CucumberStudio](https://cucumber.io/tools/cucumberstudio).

## _Pros of CucumberStudio_
- **Collaboration**: Stakeholders, product owners, and developers can all work together on specifications.
- **Gherkin Syntax Support**: CucumberStudio supports writing tests in Gherkin, a simple human-readable language for defining test cases and requirements.
- **Version Control**: Tracks changes in feature files and provides version history.
- **Integrations**: Seamlessly integrates with the **Cucumber framework** for automation and execution of tests written in Gherkin and CI/CD pipelines.
- **Reporting**: Provides test execution reports that visualize the success or failure of BDD scenarios.
- **Integration with Other Tools**: CucumberStudio integrates with other tools such as Jira, Slack, GitHub, and GitLab, enhancing collaboration and workflow.
- **Live Collaboration**: Real-time collaboration allows multiple team members to work on scenarios simultaneously, making it easier to write, review, and update test cases.

## _Cons of CucumberStudio_
- **Learning Curve for New Users**: For teams unfamiliar with Behavior-Driven Development (BDD), there may be a learning curve to effectively write Gherkin scenarios and understand the CucumberStudio workflow.Some users may find it challenging to set up automation or integrate it with other tools.
- **Complex Setup for Users**: Configuring CucumberStudio can be complicated and require additional setup time for integrating with other systems or automating workflows.
- **Compatibility issue**: There are compatibility issues faces while setup & execute the script.

  e.g. - First, i installed the latest Ruby version [3.4.1-2 (x64)](https://rubyinstaller.org/downloads/) & try to extract the feature file from `cmd` won't able to do it but later on i installed the old [2.6.0_1 (x64)](https://rubyinstaller.org/downloads/) finally i am able to extract the feature file folder.

- **Pricing**: CucumberStudio offers different pricing tiers, which can become expensive, especially for smaller teams or startups. The full range of features might be locked behind higher-tier plans.
- **Dependency on Cucumber Framework**: CucumberStudio is tightly integrated with the Cucumber testing framework, which could limit its use for teams that don't already use or prefer another testing framework.
- **Cloud-Based Dependency**: Since CucumberStudio is a cloud-based tool, teams may face issues related to internet connectivity, and there could be security concerns related to storing test cases in the cloud.

# How to setup & execute automate run
Below is a comprehensive guide on how to implement CucumberStudio in your project:

### Step 1. **Setup Eclipse**
1. Download **Eclipse**
2. Setup a new project as `maven`
3. Install cucumber plugin

### Setp 2. **Setting Up CucumberStudio**
To implement CucumberStudio in your project, follow these steps:
1. Go to [CucumberStudio](https://cucumber.io/tools/cucumberstudio) and sign up for an account.
2. If your organization already uses CucumberStudio, request an invite to join the organization.

#### Step 3: **Create a New Project**
1. Once logged in, you can create a new project by clicking on the `Create Project` button.
2. Name your project
3. Set up your team’s roles and permissions (optional), so that users can collaborate on feature files.

#### Step 4: **Add Users and Assign Roles**
Add team members to the project. You can assign them different roles like:
   - **Editor**: Can edit and manage features.
   - **Viewer**: Can only view and comment on features.
   - **Admin**: Has full control over the project.

#### Step 5: **Create Feature Files**
1. Navigate to the "Features" section within your project.
2. Click the "Create" button to create new features.
3. Define your **Feature** and **Scenarios** using Gherkin syntax. 
   Example:
   ```gherkin
   Feature: Automate calculator on real device
     Scenario: Addition of two integer value
      Given I have two integers 5 and 3
      When I add the two integers
      Then the result should be 8
   ```

#### Step 6: **Create new test run**
1. Go to "Test runs" section within your project
2. "Add new" test run

#### Step 7: **Export project**
1. Go to "Automation" tab on CucumberStudio
2. Export project in your preferred language & framework in this following case we select `Cucumber/java`
3. Unzip `project_export` folder

#### Step 8: **Install hiptest publisher**
##### What is hiptest-publisher: 
`hiptest-publisher` is a command-line tool used to publish test results and feature files from a local machine to the Hiptest platform (now known as CucumberStudio after rebranding). Hiptest/CucumberStudio is a collaborative platform for Behavior-Driven Development (BDD) that helps teams write and manage test scenarios in Gherkin syntax.

- Note: Before installing `hiptest-publisher` `ruby` should be installed to your system & path should be added.

1. Open cmd & type `gem install hiptest-publisher`
2. Check version `hiptest-publisher --version`

#### Step 9: **Fetch test run**
1. Now fetch the test run we created on **CucumberStudio**
2. Open cmd & go to under `project _export`
3. Then type `hiptest-publisher --config=hiptest-publisher.conf --without=actionwords --test-run-id=(id of the test run)`
4. Id of the test run is found under "Test runs" tab on **CucumberStudio**
5. Again run the same command with id you get from the previous command in cmd
6. Now open the feature. file & copy all the scenarios
7. Paste them in a Eclipse file under `src/main/resources` with  `.feature` extension

- Note - After running that cmd commands feature file displayed scenarios in gharkin syntx along with `uuid`.
 
#### Step 10: **Add Step Definitions**
1. After adding feature files to eclipse, run the feature file to get step definitions methods
2. You'll need to write step definitions that will link Gherkin steps to automation code (e.g., Selenium or Appium).
3. Define the step definitions in the language of your choice (e.g., Java, Ruby, JavaScript).
4. For each step (Given, When, Then), write the corresponding code in your test.

#### Step 11: **Execute runner file**
1. Once step definitions linking & implementation is done.
2. Run the runner file to generate report

- Note: Define plugin to generate report in junit .xml format: `plugin = {"pretty", "junit:target/reports/Apidemo_1.xml"}` 

#### Step 12: **Push report to CucumberStudio**
1. Once run is successfull
2. Copy report from Eclipse
3. Paste under the unzip `project_export` in a folder
4. Open cmd & type the follwing commands

- First command: 
`hiptest-publisher --config-file hiptest-publisher.conf --push "Automate_report/*.xml" --test-run-id 1032566 --push-format junit`

- Alternate command:
`hiptest-publisher --config-file=hiptest-publisher.conf --test-run-id=1032566 --push="Automate_report/*.xml" --push_format="junit" --execution-environment="Default"`

5. Your test status is updated automatically on CucumberStudio once you get the follwing output:

![image](https://github.com/user-attachments/assets/054bbe3b-c54a-4084-a172-617886fcf85e)
![image](https://github.com/user-attachments/assets/cf583126-f829-4678-b2ab-4d9ada033298)

----
## **Best Practices for Implementing CucumberStudio**

#### Keep Scenarios Simple and Clear
- Use **simple, clear language** to describe behavior. Scenarios should be easy to understand by both technical and non-technical stakeholders.
- Avoid complex logic in feature files. Keep them readable and maintainable.

#### Use Tags for Better Management
- Use tags like `@smoke`, `@regression`, or `@performance` to categorize and execute tests based on test cycles.
- **Example**:
  ```gherkin
  @regression
  Scenario: Valid user login
  ```
#### Modularize Step Definitions
- Break down step definitions into smaller, reusable methods. This will reduce duplication and increase maintainability.
  
#### Version Control and History
- CucumberStudio offers versioning to keep track of changes made to feature files. You can always roll back to previous versions if necessary.
---  

## Pricing 
As per the pricing details on the [CucumberStudio website](https://smartbear.com/product/cucumberstudio/pricing/), the platform starter at $32 per month for a single user.This plan includes:
- **Gherkin editor**
- **Test automation**
- **Advanced living documentation**
- **Feature history**
- **3 projects**
- **2 free read-only users**

While these features are useful for teams practicing Behavior-Driven Development (BDD), the cost of $32 per month may be considered high, especially for smaller teams or organizations with limited resources. Cnsidering the pricing structure, CucumberStudio may be viewed as costly, especially for smaller teams or companies with budget constraints.
