# Jenkins Python CI Demo

A small Python project for demonstrating a GitHub-to-Jenkins CI pipeline. Each push can trigger Jenkins to install dependencies and run pytest.

## Files

- `main.py`: adds two numbers
- `test_main.py`: checks the addition function
- `Jenkinsfile`: Jenkins Pipeline definition
- `requirements.txt`: pytest dependency

## Run locally

```bash
python -m pip install -r requirements.txt
python -m pytest -q
```

## Jenkins setup

Create a Pipeline job named `python-ci-demo`, select **Pipeline script from SCM**, choose Git, and enter this repository's HTTPS URL. Set branch to `*/main` and script path to `Jenkinsfile`.

For push-triggered builds, configure a GitHub webhook to `http://YOUR_EC2_PUBLIC_IP:8080/github-webhook/` and select **Just the push event**. In the Jenkins job, enable **GitHub hook trigger for GITScm polling**. Restrict Jenkins web access (port 8080) in the EC2 security group to your own IP; configure webhook reachability separately for the course demo.
