# DOCKER BUILD WORKFLOW

1.  **Pre-Flight**:
    - Check if `Dockerfile` exists. If not, trigger **Ops Manager** to create one.
    - Check `.dockerignore`.

2.  **Build**:
    - Command: `docker build -t app-local .`
    - Monitor for build errors.

3.  **Optimization Check**:
    - Trigger **Ops Manager** to analyze the build logs.
    - Did the build take too long? Suggest cache optimization.
    - Is the image size too large? Suggest pruning layers.

4.  **Security Scan (Optional)**:
    - If `trivy` or `docker scout` is installed, run a vulnerability scan on the image.

5.  **Cleanup**:
    - Ask user: "Remove the test image to save space?"