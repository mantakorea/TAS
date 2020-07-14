### Branch Strategy for test code management

![Github Test Project Branch Structure](https://github.com/ocean-network-express/OTSK-TAS-RESOURCE/blob/master/images/github-testproject-branch2.png)

***

1. Basically, TAS test script codes follow [Git flow v2](https://docs.google.com/presentation/d/10c6cw5VZp4bYIwEdA-MdO2hxoVyn12Qu5cxtrLHV3BY/edit#slide=id.p6).
1. Each test project has four branches. dev, test, release(stage), and master
1. All test codes are finally merged to master branch
1. All pull request should pass code review on github with peer review ( all branches will be locked to prevent private merge)
1. Test code merge for each branch
    * Test code change in working(or feature) branch should be merged to dev branch after application binary(ex. eCOM) is deployed to dev environment. It will prevent test fail by test change.
    * Test code change in dev branch should be merged to test branch after application is deployed to test environment
    * Test code change in test branch should be merged to release branch after application is deployed to stage environment
    * Test code change in release branch should be merged to master branch after application is deployed to prod environment

***

### Each github test project should have



    * Make four test set on TestProject (dev, test, release, master)
        Test set means a coded test in test project of TestProject. It is the unit of deployment by jenkins.
        The required test set can be selected by project's requirement. For example, automated testing can used for dev and stage. In this case, dev & stage test set will be created. 
    * Make four test jobs on TestProject (DEV, TEST, STAGE, PROD) : 
        If the size of job is large, it can be separated into multiple jobs to allocate multiple agents.

      Each test job is mapped to the actual running environment

***

### Test Project Deployment (Github -> TestProject) Structure


![Test Code Deployment Diagram](https://github.com/ocean-network-express/OTSK-TAS-RESOURCE/blob/master/images/github-testproject-testjob.png)

