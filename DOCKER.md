# Running the assignments with Docker

The homework for Big Data Platforms is a set of Jupyter notebooks that are graded
automatically. To make sure your code runs the same way on your machine and on the
grading server, the course provides a Docker image with everything installed. This
page walks through using it.

It is based on the course's own *Big Data Platforms homework guide* (dated 2026-08-24),
a copy of which is in this repo at
`Assignments/Introduction to Spark + RDD Programming/BigDataPlatforms.pdf`. If this page
and the guide ever disagree, follow the guide.

## Quick reference

```bash
docker --version                                  # must be 20.10 or newer
docker pull hainingt/big_data_platforms:2026      # once

cd path/to/the/assignment/folder
docker run --name bdp_homework --rm -p 8888:8888 -v "$(pwd):/home/jovyan/work" hainingt/big_data_platforms:2026
```

Then open the `http://127.0.0.1:8888/?token=...` link that the container prints.
Stop it with `Ctrl+C`. The Windows versions of the `run` command are in step 3.

## 1. Install Docker

- **Windows:** install Docker Desktop, then launch it from the Start menu.
- **macOS:** install Docker Desktop, then launch it from Applications.
- **Linux:** follow the instructions on the Docker site for your distribution.

Check the version, which must be **20.10 or newer**:

```bash
docker --version
```

## 2. Get the homework files

The course releases the homework files on its own schedule; the guide points to a
shared Google Drive for them. The assignment folders in this repo's `Assignments/`
directory hold the same notebooks and sample data.

Each notebook reads its data files by relative name (for example
`socialgraph_sample.dat`), so the notebook and its data have to sit in the same
folder. That decides which folder you start the container from: pick the folder that
holds the notebook you're working on.

| Work on | Start the container from |
|---------|--------------------------|
| `intro.ipynb` | `Assignments/Introduction to Spark + RDD Programming/Intro` |
| `GeoProcessor.ipynb` | `Assignments/Introduction to Spark + RDD Programming/RDD` |
| `AirTrafficProcessor.ipynb` | `Assignments/dataframe` |
| `GamingProcessor.ipynb` | `Assignments/Mllib` |
| `SocialGraph.ipynb` | `Assignments/Graphframes` |
| `trail_camera.ipynb` | `Assignments/StructuredStreaming` |
| `MusicRecommender.ipynb` | `Assignments/Extra` |

The guide warns that spaces or unusual characters in the folder path can cause
problems. The `Introduction to Spark + RDD Programming` folder name has both spaces and
a `+`. If you hit trouble, copy the notebook and its data to a simply named folder
(for example `~/bdp/rdd`) and start the container from there.

## 3. Pull the image and start Jupyter

Pull the image. You only need to do this once:

```bash
docker pull hainingt/big_data_platforms:2026
```

Open a terminal in the assignment folder and start the container. Use the command for
your shell, and enter it as **one line with no line breaks**.

**Windows Command Prompt (cmd.exe):**

```bat
docker run --name bdp_homework --rm -p 8888:8888 -v "%cd%:/home/jovyan/work" hainingt/big_data_platforms:2026
```

**Windows PowerShell:**

```powershell
docker run --name bdp_homework --rm -p 8888:8888 -v "${PWD}:/home/jovyan/work" hainingt/big_data_platforms:2026
```

**macOS / Linux (bash, zsh, and so on):**

```bash
docker run --name bdp_homework --rm -p 8888:8888 -v "$(pwd):/home/jovyan/work" hainingt/big_data_platforms:2026
```

What the options do:

| Option | Meaning |
|--------|---------|
| `--name bdp_homework` | Names the container so you can stop it by name later |
| `--rm` | Deletes the container when it stops (your files are kept, see below) |
| `-p 8888:8888` | Makes Jupyter reachable at port 8888 on your machine |
| `-v <folder>:/home/jovyan/work` | Mounts your current folder inside the container as `work` |

The quotes around the `-v` value are an addition to the guide's version of these
commands. They keep the command working if the path contains a space.

## 4. Open Jupyter and do the work

1. The terminal prints a link like `http://127.0.0.1:8888/?token=<TOKEN_VALUE>`. Copy
   the whole link, token included, into your browser.
2. Open the `work` folder in Jupyter. That is the folder you started the container
   from, so your notebook and data files are there.
3. Open the notebook and work on it. Changes are saved straight into your local folder.

### Rules for the notebooks

The assignments are graded automatically, so:

- Only change the code cells marked `YOUR CODE HERE` or `YOUR ANSWER HERE`.
- **Don't add or remove cells**, and don't change the structure of the notebook.
- Don't rely on extra packages. The container has what the assignments need.
- Before submitting, choose **Kernel → Restart & Run All** and check that everything
  runs without errors.
- There are **hidden test cases** on the server. Passing every visible check locally
  doesn't guarantee a full score, so test your code carefully.

## 5. Submit

1. Go to the **big-data-platforms-26** MOOC page and sign in with your MOOC account.
2. Find the submission box at the bottom of the page, choose the assignment title, and
   upload your notebook (`.ipynb`) file.

The notebook is saved in the folder you started the container from. You can also
download it from Jupyter with **File → Download as → Notebook (.ipynb)**.

## 6. Get feedback

- The server grades submissions **once an hour**.
- Your overall score appears on the MOOC page.
- Detailed feedback is emailed to the address you registered your MOOC account with,
  from `bigdata.platforms.feedback@gmail.com`. Check your spam folder if it doesn't
  arrive.
- You can submit as many times as you like. **Only your best score is recorded.**

## 7. Stop the container

Press `Ctrl+C` in the terminal where the container is running. If it is running in the
background, stop it with:

```bash
docker stop bdp_homework
```

Because of `--rm`, the container is deleted when it stops. Your notebooks are not lost:
they live in your local folder, not inside the container.

## Troubleshooting

**Jupyter doesn't show my files, or I can't save.**
The container may not have permission to use the folder. From inside the assignment
folder, run the guide's fix before starting the container:

```bash
chmod 777 -R .
```

That makes everything under the current folder writable by everyone, so run it only
inside the assignment folder, never in a folder with other things in it. On Docker
Desktop (Windows or macOS), also check its settings: you may need to grant it access
to the folder explicitly.

**`port is already allocated` or the page won't load.**
Another program, often another Jupyter container, is already using port 8888. Stop
it, or use a different port on your side:

```bash
docker run --name bdp_homework --rm -p 8889:8888 -v "$(pwd):/home/jovyan/work" hainingt/big_data_platforms:2026
```

Then open the printed link but change `8888` to `8889` in the address.

**`The container name "/bdp_homework" is already in use`.**
A previous container with that name is still running. Stop it with
`docker stop bdp_homework` and run the command again.

**Problems with the folder path.**
Spaces or illegal characters in the path can break the mount. Move the files to a
simpler path, or use the full absolute path in the command.

**Anything else.**
Contact the course staff on Telegram or at `bigdata-platforms-f26@helsinki.fi`.

## Working outside Docker

If you can't run Docker, `requirements-assignments.txt` in the root of this repo gives
a best-effort local Python setup, and the root `README.md` explains what it does and
doesn't cover. The auto-grader uses the Docker environment, so check your final answers
in the image before submitting.
