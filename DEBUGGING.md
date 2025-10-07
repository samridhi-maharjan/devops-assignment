## Assignment 1 working pipeline explaination 

My project is a simple Node.js “Hello World” app. The main file app.js just logs a message to the console:<br>
console.log("Hello World");

I created a Dockerfile to containerize the app, and a GitHub Actions workflow file (.github/workflows/build.yml) to automate testing and building.

- ## Workflow Explanation:<br>
The workflow is triggered on every push to the main branch.<br><br>
It contains two jobs:<br>

- # test-job<br>
Runs node app.js as a simple test to verify the app runs without crashing.
If this job fails, the workflow stops immediately.

- # build-job: <br>
Uses the needs: test-job keyword, meaning it only runs if the test-job succeeds.
Builds the Docker image using docker build . to ensure the Dockerfile is valid.

- # The needs: Keyword<br>
The needs: keyword creates a dependency between jobs.
It ensures that the build-job waits for the test-job to pass successfully before starting.
If the test fails, the dependent job (build-job) will not run.
