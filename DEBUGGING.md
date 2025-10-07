## Assignment 1 working pipeline explaination 

My project is a simple Node.js “Hello World” app. The main file app.js just logs a message to the console:<br>
console.log("Hello World");

I created a Dockerfile to containerize the app, and a GitHub Actions workflow file (.github/workflows/build.yml) to automate testing and building.

- Workflow Explanation <br>
The workflow is triggered on every push to the main branch.<br><br>
It contains two jobs:<br>

- test-job <br>
Runs node app.js as a simple test to verify the app runs without crashing.
If this job fails, the workflow stops immediately.

- build-job: <br>
Uses the needs: test-job keyword, meaning it only runs if the test-job succeeds.
Builds the Docker image using docker build . to ensure the Dockerfile is valid.

- The needs: Keyword<br>
The needs: keyword creates a dependency between jobs.
It ensures that the build-job waits for the test-job to pass successfully before starting.
If the test fails, the dependent job (build-job) will not run.


---

## Assignment 2: Break and Fix Challenge
<img src="/images/error.png">

<b>What the error means <br>
Docker couldn’t find the image node:22-samridhi on Docker Hub. This happened because the image tag I wrote doesn’t exist. Since Docker can’t find a valid base image, it couldn’t build my app.

<b>How I fixed it?<br>
I updated the Dockerfile to use a valid Node.js image tag.After pushing this fix, the workflow ran successfully and the build-job passed.
<br>
<img src="/images/sucess.png">

- **Failed workedflow run**: [link] (https://github.com/samridhi-maharjan/devops-assignment/actions/runs/18317843045)
- **Sucessful workflow run**: [link] (https://github.com/samridhi-maharjan/devops-assignment/actions/runs/18319769142)
