This Docker image is designed for processing SVG data files and is exclusively intended for CMU's CERLAB ShapeAnalysis team.

In theory, Docker commands should be naturally supported on most Linux machines. If your Linux machine does not support docker commands, try to visit the <a href="https://docs.docker.com/engine/install/ubuntu/" target=_blank> official website</a> to download Docker on your machine.

To pull this Docker image, on a Linux machine, run:

```
docker pull lingta/svgparser
```

Due to the limitation of Docker, this image is intended to run with Docker Volume. For more information about Docker Volume, please visit https://docs.docker.com/storage/volumes/

The revised version of the SVG parser as a Docker image will no longer support user input for reading and writing directories. Instead, the only input required from the user is to specify the directory that needs to be mounted inside the Docker container. By using Docker Volume, the Docker container will fetch the SVG data files from the mounted directory and output the results back to the same mounted directory.

The content of the mounted directory should strictly follow these rules:

<ul>
<li> The directory should contain two subdirectories, one named 'input-data' and the other named 'results'.</li>
<li> Inside the 'input-data' directory, only SVG files should be placed. Any files have the extension other than ".svg"  will be ignored.</li>
<li> The 'results' directory is where all the output .txt files are located after parsing is done</li>
</ul>

The mounted directory should look like this:

```
<mounted_directory>
├── input-data
│      ├── 1.svg
│      ├── 2.svg
│      ├── ...
├── results
```

To start the parser, run the command

```
docker run -v <mounted_directory_path>:/data lingta/svgparser
```

The mounted directory path should be a Linux absolute path such as

```
/home/user/myFolder
```
