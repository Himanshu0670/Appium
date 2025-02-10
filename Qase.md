
## [Qase Test Management Tool](https://qase.io/?utm_medium=cpc&utm_source=google&utm_term=qase&utm_campaign=Search_Brand_Beta&hsa_acc=1263669945&hsa_cam=21553353806&hsa_grp=164381836014&hsa_ad=708283550380&hsa_src=g&hsa_tgt=kwd-449732425801&hsa_kw=qase&hsa_mt=p&hsa_net=adwords&hsa_ver=3&gad_source=1&gclid=Cj0KCQiA19e8BhCVARIsALpFMgE4hJsD9IG7x91uoSWPMt8phOBLayWBCNL-1OJT8-kh2N2F41PU4REaAkcVEALw_wcB)
Qase is a modern test management tool designed to help software teams plan, manage, and track their testing efforts. It supports both manual and automated testing, offering an intuitive platform that simplifies test management, improves collaboration, and enhances the overall testing workflow. Qase is suitable for agile teams, quality assurance professionals, and developers, helping them maintain high-quality standards throughout the software development lifecycle.Here is the page link link of detailed documentation of [Qase](https://docs.qase.io/).

### Key Features :-

1. **Test Case Management:**
   - Allows users to create, edit, and organize test cases in a structured way.
   - Supports reusable test steps and categories for better organization.
   - Test cases can be grouped by projects, versions, and milestones.

2. **Test Run Management:**
   - Teams can create and execute test runs based on test cases, track the execution status, and manage results in real-time.
   - Test runs can be created manually or linked to automated testing scripts.
   
3. **Collaboration Tools:**
   - Supports team collaboration with features like comments, tagging team members, and attaching files for easy communication.
   - Integrated with popular collaboration platforms like Jira.

4. **Integration with CI/CD:**
   - Integrates seamlessly with CI/CD tools like GitHub, GitLab, Jenkins, and more.
   - Automatically syncs test results from automated tests, providing a clear overview of test status within the development pipeline.

5. **Reporting & Analytics:**
   - Generates detailed test execution reports, providing insights into test coverage, results, and trends.
   - Customizable dashboards and analytics help teams track the overall quality metrics and test progress.

6. **Version Control:**
   - Tracks test case versions, allowing teams to see changes made over time.
   - Helps teams maintain consistent and up-to-date testing processes as software evolves.

7. **Test Automation Support:**
   - Qase integrates with popular test automation frameworks and tools like Selenium, Appium, and Cypress.
   - Automated test results can be imported into Qase for centralized reporting.

8. **User-Friendly Interface:**
   - Intuitive, easy-to-navigate interface with drag-and-drop capabilities for test organization.
   - Provides a simple onboarding process for new users and teams.

9. **Permissions & Role Management:**
    - Granular access control for teams, allowing administrators to manage permissions based on roles.
    - Enables control over who can create, edit, and execute test cases or view reports.

### Benefits :-
- Increased test management efficiency and organization.
- Improved collaboration between testers, developers, and project managers.
- Better visibility into the testing process and overall product quality.
- Flexible and adaptable to various team sizes and project requirements.

Qase’s comprehensive feature set helps streamline the software testing process, ensuring teams can deliver high-quality software faster and more efficiently.

### [Pricing](https://qase.io/pricing) :-
The pricing page on Qase.io outlines the different subscription plans available for users, tailored to different needs and team sizes. Here's a summary of the plans and features offered:

1. **Free Plan:**
   - Ideal for small teams or individual users.
   - Includes basic features like -
      - Up to 3 user
      - 2 project
      - 500 mb storage
      - 30 days of test data history
      - 25k test results/mo via API
   - Supports manual testing only with limited access to reporting and integration features.

2. **Startup Plan:**
   - Designed for small to medium teams.
   - Costs a fixed amount $20 (billed annually or monthly).
   - Includes features like -
      - Up to 20 users
      - Unlimited test runs & projects
      - 100 Gb storage
      - 90 days of test data history
      - Dashboards & reporting
      -  35+ integrations
      -  100k test results/mo via API
   - Additional features like Jira integration, test case versioning, and access to custom workflows.

Their are two more plans named as **Professional Plan & Enterprise Plan** you can read the detailed description on [Pricing](https://qase.io/pricing) page.

### [Company that uses Qase](https://theirstack.com/en/technology/qase-io)
---

## How to integrate Qase with Cypress to Automate Testcase
To integrate Qase Reporter in your Cypress setup, follow these steps:

### Step 1: Activate the Cypress App
- To activate the app, go to the Qase `Apps` section in your workspace, and click on ‘Activate’.
- Switch to the ‘Access tokens’ tab, and create a new API token. Save the API token as we’ll need it for the next steps.

#### Note: I assuming that cypress is installed on your system. 

### Step2: Add cypress-qase-reporter to your project
To install and add the reporter as a development dependency, run the following in your node project:
- `npm install -D cypress-qase-reporter`

### Step3: Add cypress-multi-reporters  as well to your project
To install and add the reporter as a development dependency, run the following in your node project:
- `npm install cypress-multi-reporters`

### Step4: Add API token & Test case ID
At the very least, copy paste the mention code to `cypress.config.js`  file, & reporter will need two variables defined - your Cypress App’s Token, and the Qase Project you want to publish the results to.

```
const cypress = require('cypress');
const qasePlugin = require('cypress-qase-reporter/plugin');
const qaseMetadata = require('cypress-qase-reporter/metadata');

module.exports = {
    reporter: 'cypress-multi-reporters',
    reporterOptions: {
        reporterEnabled: 'cypress-qase-reporter',
        cypressQaseReporterReporterOptions: {
            mode: "testops",
            debug: true,
            testops: {
                api: {
                    token: '<app-token>',  // Replace with your Cypress app token
                },
                project: '<prj-code>',  // Replace with your Qase project code
                uploadAttachments: true,
                run: {
                    complete: true,
                },
            },
            framework: {
                cypress: {
                    screenshotsFolder: 'cypress/screenshots',
                }
            }
        },
    },
    video: false,
    e2e: {
        setupNodeEvents(on, config) {
            qasePlugin(on, config);
            qaseMetadata(on);
        },
    },
};
```

### Step5: Write Test case & cypress script 
Add test cases to Qase app & write cypress script, here is a demo script: 

```
describe('Automationteststore', () => {
  beforeEach(() => {
    cy.visit('https://automationteststore.com/');
  });

  // Note - Write exactly same title name of Testcase in it().
    it('Visit to the web application', () => {
      cy.log('CIWQ-1'); //Write exactly same Test case ID/      
      cy.url().should('include', '.com'); 
    });

    it('Select Men section', () => {
 //Test ID 2
      cy.log('CIWQ-3');
      cy.get('[href="https://automationteststore.com/index.php?rt=product/category&path=58"]').click();
      cy.get('.breadcrumb').should('contain.text','	    	Men	    ');
    });

    it('Select Skincare category', () => {
//Test ID 3      
      cy.log('CIWQ-4');
      cy.get('[href="https://automationteststore.com/index.php?rt=product/category&path=58"]').click();
      cy.get('.mt10.align_center').eq(3).should('contain.text','Skincare').click()

    });

});
````

### Step6: Execute cypress script 
To run only a specific script from terminal run
- `npx cypress run --spec "cypress/integration/myTest.spec.js"`

To run all scripts from terminal run
-  `npx cypress run`
