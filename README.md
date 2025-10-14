<<<<<<< HEAD
# CI/CD Jenkins

- [CI/CD Jenkins](#cicd-jenkins)
  - [Intro to CI/CD and Jenkins](#intro-to-cicd-and-jenkins)
    - [What is CI?](#what-is-ci)
    - [Benefits of CI?](#benefits-of-ci)
    - [What is CD?](#what-is-cd)
    - [What is Jenkins](#what-is-jenkins)
    - [Why use Jenkins? Benfits? Disadvantages?](#why-use-jenkins-benfits-disadvantages)
    - [Stages of Jenkins for a CI/CD pipeline](#stages-of-jenkins-for-a-cicd-pipeline)
    - [What alternatvies are there for Jenkins](#what-alternatvies-are-there-for-jenkins)
    - [Why build pipeline? Business value?](#why-build-pipeline-business-value)
    - [Diagram of CI/CD](#diagram-of-cicd)
    - [Diagram of how CI/CD pipeline on Jenkins works](#diagram-of-how-cicd-pipeline-on-jenkins-works)

## Intro to CI/CD and Jenkins


### What is CI? 
- Continuous Integration
- Triggered by: Developers that are frequently pushing their code changes to a shared repo.
- Tests are automatically run on the updated code 
  - if the tests pass, the code is integrated /mergred with the main code branch.

### Benefits of CI?
- Helps to quickly identify and resolve integration bugs early
  - reduces cost and complexity of project management
- Helps to maintain a stable and functional software build

### What is CD? 
- Continuous Delivery or Continuous Deployment
  - The software is always in a deployable state and CAN be pushed into production at any time
  - Often involves producing a deployable artifact. (code bundled together)
  - Used when we want human intervention (someone to make a decision on when to deploy/release the artificat)
- Continuous Deployment
  - Usally still produces a deployable artifact, but also automatically deploys it, often to production
  - Benefits of CD?
    - Removal of human approval, so deployment is automated

### What is Jenkins
- An open-source  automation server
- Primarily used for CI/CD but can automate much more..

### Why use Jenkins? Benfits? Disadvantages?
- Automation of CI/CD helps to avoid human error and reduce manual interventions
- Extensibility: has over 1800+ plugins, to support variety of tools and programming languages
- Scalability: can add worker nodes/agents to handle the jobs and projects that need to be run
- Community support
- Customisation
- Cross-Platform e.g Windows, Linux, MacOS

Benefits
- regular feedback from users allows for bugs to be resolved more quickly

Disadvantages
- Complex for beginners, depending on configuration and setup
- Maintenace overhead
  - managing the plug-ins etc
- GUI interface not so modern
  
### Stages of Jenkins for a CI/CD pipeline
1. Source code management (SCM)
2. Build eg. compile the code
3. Testing
4. Package into deployable artifact
5. If Continuous Deployment, then deploy
6. Monitoring: setting up/integrating the application with monitoring/logging tools

### What alternatvies are there for Jenkins
- Github Actions
- GitLab CI
- CircleCI
- Travis CI
- Bamboo
- TeamCity
- GoCD
- Azure Pipelines

### Why build pipeline? Business value?
- Faster time to market
  - users see the value straight away
  - buisiness benefits as a result
- Good for iterative testing quickly
- Improved quality of software by catching bugs earlier
- Productivity of developers: they can concentrate on development (writing code)

### Diagram of CI/CD
Starts with a trigger (need a webhook): git push (dev)
1. Test
2. Merge
This is the CI part of CI/CD
3. Deploy
This is the CD part of CI/CD

### Diagram of how CI/CD pipeline on Jenkins works
1. You are the developer (dev), you trigger the pipeline with a ```git push``` on the dev branch
2. This uploads the changes to the Github repo.
3. Github uses a webhook (link to info here) to notify Jenkins of the change.
   -  Jenkins needs to be listening out for the notification
4.  Jenkins is made up of a master node which uses:
    -  agent/worker nodes
        -  these are responsible for running the jobs (Test--> Merge-->Deploy)
        -  if the test passes, it will then merge the code from the dev to the main branch.
           -  the master node will use SSH to merge the code, so will need our private key
        -  if the merge is successful, it will then deploy the code to the EC2 instance
             -  it will also SSH into the EC2 instance to deploy the code, so will need the .pem file to authenticate
     -  Jenkins can also run the jobs without worker nodes if needed
 