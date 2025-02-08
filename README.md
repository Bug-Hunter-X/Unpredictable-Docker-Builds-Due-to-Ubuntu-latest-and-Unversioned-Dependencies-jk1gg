# Unpredictable Docker Builds Due to `ubuntu:latest` and Unversioned Dependencies
This repository demonstrates a common yet often overlooked issue in Dockerfiles: using the `latest` tag for base images and installing Python packages without specifying versions.  This can lead to unpredictable build behavior, especially in CI/CD environments where the base image and package versions may change unexpectedly.

The original `Dockerfile` uses `ubuntu:latest` and installs Python packages without pinning versions.  This makes the build non-deterministic and can easily break between builds.

The solution `Dockerfile.fixed` addresses this problem by specifying a concrete version for the `ubuntu` base image and using the `pip install -r requirements.txt` command for python packages to specify versions.

This ensures that the build remains consistent and reproducible across different environments.