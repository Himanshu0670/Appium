# What is CucumberStudio
[CucumberStudio](https://support.smartbear.com/cucumberstudio/docs/index.html) is a collaborative testing platform in the cloud that allows the software delivery team to co-design acceptance tests. It provides a real-time environment for designing, executing and refactoring tests. Ultimately CucumberStudio enables to automate tests that become the living specification of your Apps.
CucumberStudio is intended to be used by everyone in a software delivery team: customers, domain experts, product managers, testers and developers.

## Prerequisites

- Download [Java](https://www.oracle.com/in/java/technologies/downloads/)
- Download [Eclipse](https://www.eclipse.org/downloads/)
- Add dependencies under [pom.xml](https://mvnrepository.com/)
-  

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
- **Compatibility issue**: There are high chances 
- **Pricing**: CucumberStudio offers different pricing tiers, which can become expensive, especially for smaller teams or startups. The full range of features might be locked behind higher-tier plans.
- **Dependency on Cucumber Framework**: CucumberStudio is tightly integrated with the Cucumber testing framework, which could limit its use for teams that don't already use or prefer another testing framework.
- **Limited Non-Technical Stakeholder Support**: While Gherkin makes it accessible to non-technical stakeholders, they may still struggle with complex scenarios or issues if the scenarios are not well-written or maintained.
- **Cloud-Based Dependency**: Since CucumberStudio is a cloud-based tool, teams may face issues related to internet connectivity, and there could be security concerns related to storing test cases in the cloud.


Below is a comprehensive guide on how to implement CucumberStudio in your project:

### 2. **Setup Eclipse**
1. Download **Eclipse**
2. Setup a new project as `maven`
3. Install cucumber plugin

### 2. **Setting Up CucumberStudio**
To implement CucumberStudio in your project, follow these steps:

#### Step 1: **Create an Account**
1. Go to [CucumberStudio](https://cucumber.io/tools/cucumberstudio) and sign up for an account.
2. If your organization already uses CucumberStudio, request an invite to join the organization.

#### Step 2: **Create a New Project**
1. Once logged in, you can create a new project by clicking on the "Create New Project" button.
2. Name your project, and select the type of project (e.g., Web, Mobile).
3. Set up your team’s roles and permissions (optional), so that users can collaborate on feature files.

#### Step 3: **Add Users and Assign Roles**
1. Add team members to the project. You can assign them different roles like:
   - **Editor**: Can edit and manage features.
   - **Viewer**: Can only view and comment on features.
   - **Admin**: Has full control over the project.

#### Step 4: **Create Feature Files**
1. Navigate to the "Features" section within your project.
2. Click the "Create New Feature" button.
3. Define your **Feature** and **Scenarios** using Gherkin syntax. 
   Example:
   ```gherkin
   Feature: Automate calculator on real device
     Scenario: Addition of two integer value
      Given I have two integers 5 and 3
      When I add the two integers
      Then the result should be 8
   ```

#### Step 5: **Create new test run**
1. Go to Test runs tab on CucumberStudio
2. Add new test run

#### Step 6: **Export project**
1. Go to Automation tab on CucumberStudio
2. Export project in your preferred language in this following case we select `Cucumber/java`
3. Unzip `project_export` folder

#### Step 7: **Install hiptest publisher**

##### What is hiptest-publisher: 
`hiptest-publisher` is a command-line tool used to publish test results and feature files from a local machine to the Hiptest platform (now known as CucumberStudio after rebranding). Hiptest/CucumberStudio is a collaborative platform for Behavior-Driven Development (BDD) that helps teams write and manage test scenarios in Gherkin syntax.

- Note: Before installing `hiptest-publisher` `ruby` should be installed to your system & path should be added.

1. Open cmd & type `gem install hiptest-publisher`
2. Check version `hiptest-publisher --version`

#### Step 8: **Fetch test run**
1. Now fetch the test run we created on **CucumberStudio**
2. Open cmd & go to under `project _export`
3. Then type `hiptest-publisher --config=hiptest-publisher.conf --without=actionwords --test-run-id=(id of the test run)`
4. Id of the test run is found under Test runs tab on **CucumberStudio**
5. Again run the same command with id you get from the previous command
6. Now open the feature. file & copy all the scenarios
7. Paste them in eclipse with  `.feature` extension

#### Step 9: **Push report to CucumberStudio**

- First command: 
`hiptest-publisher --config-file hiptest-publisher.conf --push "Automate_report/*.xml" --test-run-id 1032566 --push-format junit`

- Alternate command:
`hiptest-publisher --config-file=hiptest-publisher.conf --test-run-id=1032566 --push="Automate_report/*.xml" --push_format="junit" --execution-environment="Default"`

#### Step 5: **Add Step Definitions**
1. After writing feature files, you'll need to write step definitions that will link Gherkin steps to automation code (e.g., Selenium or Appium).
2. Define the step definitions in the language of your choice (e.g., Java, Ruby, JavaScript).
3. For each step (Given, When, Then), write the corresponding code in your test automation framework.

#### Step 6: **Integrate with Automation Framework**
To run tests automatically, you'll need to integrate CucumberStudio with your test automation framework.

1. **CucumberStudio API Integration**:
   - Use the **CucumberStudio API** to programmatically upload and update feature files from your local repository.
   - Use tools like **Cucumber CLI**, **Maven**, or **Gradle** to automate tests and push test results to CucumberStudio.
   

#### Step 8: **Collaborate with Stakeholders**
1. With CucumberStudio, your product owners, developers, and testers can collaboratively:
   - Write and review feature files.
   - Track progress on features and scenarios.
   - Comment and provide feedback on scenarios in real-time.

2. CucumberStudio has a built-in discussion board to engage stakeholders for scenario elaboration, approval, or clarification.

### 3. **Best Practices for Implementing CucumberStudio**

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

#### Automate and Integrate Continuous Testing
- Integrate automated testing tools with CucumberStudio. Ensure tests are run in the CI/CD pipeline to provide fast feedback.
  
### 4. **Monitoring and Reporting**
CucumberStudio provides detailed execution reports:
- **Scenario Execution Reports**: See the outcome of each scenario, including passes and failures.
- **Historical Analysis**: Review the history of all scenarios and changes made over time.
- **Integrate with TestRail** or similar tools for end-to-end reporting.

### 5. **Advanced Features of CucumberStudio**
- **Feature flags**: Enable or disable tests based on specific flags or versions of your application.
- **Custom Test Reports**: Customize the reports to display the most relevant information for your team.
- **Advanced Integrations**: CucumberStudio supports integrations with GitHub, Jira, and other project management tools.

### Conclusion
CucumberStudio helps align teams on behavior-driven development by allowing collaboration, managing Gherkin-based specifications, and automating tests. By setting it up properly with integration into your automation framework and CI/CD pipeline, you can streamline the BDD process, gain clarity in project specifications, and automate the verification of those specifications.

## Pricing 
As per the pricing details on the [CucumberStudio website](https://smartbear.com/product/cucumberstudio/pricing/), the platform starts at $32 per month for a single user.This plan includes the **`Gherkin editor`, `test automation`, and `advanced living documentation` features such as feature history and digest. Additionally, it provides the ability to manage `3 projects` and includes `2 free read-only users`**. While these features are useful for teams practicing Behavior-Driven Development (BDD), the cost of $32 per month may be considered high, especially for smaller teams or organizations with limited resources. Cnsidering the pricing structure, CucumberStudio may be viewed as costly, especially for smaller teams or companies with budget constraints.

