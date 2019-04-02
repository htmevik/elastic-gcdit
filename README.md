# Traffic accidents
The software and data we need for this workshop is available as a Docker image. This means that the only thing you need to install locally on your computer, is Docker itself.

### Download and install Docker Community Edition:

Use the provided urls to download the install files:
- [For Windows](https://download.docker.com/win/stable/31259/Docker%20for%20Windows%20Installer.exe)
- [For MacOS](https://download.docker.com/mac/stable/31259/Docker.dmg)
- [For Ubuntu](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-18-04)

Windows users need Hyper-V in order to run Docker. This is automatically enabled when installing Docker Desktop on Windows. If you need to enable it manually, have a look at [this link](https://docs.docker.com/machine/drivers/hyper-v/)

Verify the installation by running `docker version` in Terminal or PowerShell


### Pull the Docker image

The Docker image is available on DockerHub. It's recommended that you download it before you arrive at the workshop:

- Open PowerShell (Windows) or terminal and type in the following
```docker pull oyvindbratvedt/elastic-ifi```

### Run the Docker image as a container

To run the Docker image as a container, open a PowerShell/terminal and type
 
  ```docker run --rm -p 5601:5601 -p 9200:9200 oyvindbratvedt/elastic-ifi``` 

This will start Elasticsearch in the Docker container, which will spend some time indexing the ~290000 traffic accidents, and then launch Kibana. Initially the console will output errors while it waits for Elasticsearch to be fully started. Depending on your computer, this could be 20 seconds to a couple of minutes.

When the accidents are finished indexing, you can open Kibana in your browser: http://localhost:5601

### Configure Kibana

#### Set Index Pattern
You need to point Kibana to which Elasticsearch index it should fetch data from.

- In Kibana, navigate to **Management** and click **Index Patterns**.
- Enter `accidents` in the **Index pattern** field. 
- Click **Next step**
- In **Configure settings**, select **timestamp** in the **Time Filter field name** dropdown menu.
- Click **Create index pattern**

#### Get data from further back than 15 minutes

- Navigate to **Discover**
- In the top right corner, press **Last 15 minutes**
- In the **Time Range** menu, press **Relative**
- Change the **From** field to `50 years ago`
- Click **Go**
- All the 289610 accidents in the dataset should now be visible

### Kibana
Now you can play around with the data in Kibana. Go to **Visualize** where you can create coordinate maps, graphs and plots visualizing the accidents. 

# Assignments

You are now all set up to create visualisations that will help you find answers to [the assignments!](https://github.com/htmevik/elastic-gcdit/blob/master/tasks.md)

### Visualisation Inspiration
Selecting the correct way to display your data can be quite challenging. Check out [this link](https://raw.githubusercontent.com/ft-interactive/chart-doctor/master/visual-vocabulary/poster.png) for some hints on graphs suitable for visualising many different data relationships.
