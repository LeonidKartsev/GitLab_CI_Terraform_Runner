
![Picture](https://res.cloudinary.com/qunux/image/upload/v1594405830/configure-gitlab-ci-with-gcr_opt_ek4srf.png)

# Container image tag checks and GCR publishing

---

The repository root contains the main **`.gitlab-ci.yml`** template. It ties together per-image CI jobs across the project.

Each image lives in its own directory with:

* **`.gitlab-ci.yml`**
* **`Dockerfile`**
* **`version.txt`**

Each per-directory **`.gitlab-ci.yml`** uses [crane](https://github.com/google/go-containerregistry/tree/main/cmd/crane) to verify whether the image tag already exists in **Google Container Registry (GCR)**. If the tag is absent, CI builds and pushes the image; if the tag already exists, the job fails with exit code `1` so duplicate publishes are avoided. The tag to publish is read from **`version.txt`**.

## Adding an image to Google Container Registry

---

1. Create a branch.
2. Add a directory for the new image with `Dockerfile`, `version.txt`, and related files.
3. Add a **`.gitlab-ci.yml`** in that directory (use an existing image folder as a reference).
4. Include the new directory’s CI configuration in the root **`.gitlab-ci.yml`**.
5. Push your changes and open a merge request.
6. Confirm the `build-branch` job succeeds (staging artifacts are available at this stage).
7. Merge to `master` and verify the production build artifact.
