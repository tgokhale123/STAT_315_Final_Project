# Sleep Health and Lifestyle Analysis Project

This project contains a comprehensive exploratory data analysis of lifestyle factors, physiological indicators, and sleep health patterns using a synthetic dataset of 374 individuals. The analysis explores relationships between sleep quality, stress levels, physical activity, BMI, occupation, and other health metrics using statistical modeling and bootstrap resampling techniques.

## Project Contents

- `final_project.ipynb` - Complete analysis notebook with all code, visualizations, statistical models, and detailed commentary
- `sleep_health_lifestyle.csv` - Dataset containing sleep and lifestyle metrics for 374 individuals
- `sleep_banner.png` - Banner image used in the notebook
- `Dockerfile` - Docker configuration for reproducible environment with pinned versions
- `requirements.txt` - Python package dependencies with exact version numbers
- `README.md` - This file with complete setup and usage instructions

## Prerequisites

Before starting, ensure you have:
- **Docker** installed on your system ([Install Docker](https://docs.docker.com/get-docker/))
- At least **2GB of free disk space** for the Docker image and dependencies
- A web browser (Chrome, Firefox, Safari, or Edge)

To verify Docker is installed and running:
```bash
docker --version
docker ps
```

## Building from Source (Using GitHub Repository)

If you want to build the image yourself or modify the analysis:

### Step 1: Clone the Repository

```bash
git clone https://github.com/tgokhale123/STAT_315_Final_Project.git
cd STAT_315_Final_Project
```

### Step 2: Build the Docker Image (make sure docker app is running before running this)

```bash
docker build -t sleep-health-analysis .
```

**What this does:**
- Installs Python 3.11.11-slim
- Installs all required packages with pinned versions:
  - jupyter==1.1.1
  - notebook==7.0.8
  - numpy==1.26.4
  - pandas==2.2.3
  - matplotlib==3.9.3
  - seaborn==0.13.2
  - ipython==8.31.0
  - scikit-learn==1.5.2
  - jupysql==0.11.1
  - duckdb==1.1.3
  - duckdb-engine==0.13.2
- Copies the notebook, dataset, and image files into the container
- Configures Jupyter notebook server

**Build time:** Approximately 1-4 minutes depending on your internet connection.


### Step 3: Run the Container

```bash
docker run -p 8888:8888 sleep-health-analysis
```

This command:
- Maps port 8888 from the container to your local machine
- Starts Jupyter notebook server
- Makes the notebook accessible in your browser

### Step 4: Access the Notebook

Open your web browser and navigate to:

```
http://localhost:8888
```

You should see the Jupyter notebook interface with `final_project.ipynb` available.

---

## Stopping the Container

To stop the running container:

**Option 1:** Press `Ctrl+C` in the terminal where the container is running

**Option 2:** Find and stop the container manually:

```bash
# List running containers
docker ps

# Stop the container using its ID
docker stop <container-id>
```

---

## Troubleshooting

### Port Already in Use

If port 8888 is already in use on your machine:

```bash
docker run -p 8889:8888 sleep-health-analysis
```

Then access the notebook at `http://localhost:8889` instead.

### Permission Denied (Linux/Mac)

On Linux or Mac, you may need to run Docker commands with `sudo`:

```bash
sudo docker build -t sleep-health-analysis .
sudo docker run -p 8888:8888 sleep-health-analysis
```

### Image Build Fails

If the build fails:
1. Ensure you have a stable internet connection
2. Ensure you have sufficient disk space (at least 2GB free)
3. Try cleaning up old Docker images and rebuilding:

```bash
docker system prune -a
docker build -t sleep-health-analysis .
```

### Container Starts but Browser Shows "Connection Refused"

1. Wait 10-15 seconds after starting the container for Jupyter to fully initialize
2. Verify the container is running: `docker ps`
3. Check the terminal output for any error messages
4. Try accessing `http://127.0.0.1:8888` instead of `http://localhost:8888`

---

## Package Versions

The project uses the following Python packages with pinned versions for reproducibility:

| Package | Version |
|---------|---------|
| Python | 3.11.11 |
| Jupyter | 1.1.1 |
| Notebook | 7.0.8 |
| NumPy | 1.26.4 |
| Pandas | 2.2.3 |
| Matplotlib | 3.9.3 |
| Seaborn | 0.13.2 |
| IPython | 8.31.0 |
| scikit-learn | 1.5.2 |
| jupysql | 0.11.1 |
| duckdb | 1.1.3 |
| duckdb-engine | 0.13.2 |

All versions are explicitly specified in `requirements.txt` and `Dockerfile` to ensure reproducibility.

---

## Project Structure

```
.
├── Dockerfile              # Docker configuration with pinned Python version
├── requirements.txt        # Python dependencies with exact versions
├── README.md              # This file with complete instructions
├── final_project.ipynb    # Complete analysis notebook
├── sleep_health_lifestyle.csv  # Dataset (374 rows, 13 columns)
└── sleep_banner.png       # Banner image for notebook
```

---

## Analysis Overview

The notebook provides a comprehensive exploratory data analysis addressing five key research questions:

1. **Sleep Patterns:** How much do people sleep on average, and how does that relate to their reported sleep quality?
2. **Lifestyle Factors:** What is the relationship between stress level, physical activity, and sleep quality?
3. **Health Indicators:** To what extent are physiological metrics associated with sleep health outcomes?
4. **Occupational Differences:** Are there significant differences in sleep patterns across occupational categories?
5. **Correlation Analysis:** Which lifestyle factors exhibit the strongest correlation with sleep outcomes?

### Analysis Features

The analysis includes:
- **Data Cleaning and Preparation:** Comprehensive handling of missing values, feature engineering, and data validation
- **Exploratory Data Analysis:** Publication-ready visualizations using matplotlib and seaborn
- **Bootstrap Resampling:** Nonparametric bootstrap methods (n=1000) for robust confidence interval estimation
- **Statistical Modeling:** Linear regression with bootstrap-based inference for correlation coefficients
- **Interpretation and Reporting:** Detailed commentary on findings, limitations, and future directions

### Key Findings

- Sleep duration strongly correlates with sleep quality (r = 0.88, 95% CI: 1.26-1.39)
- Stress level shows the strongest negative correlation with sleep quality (r = -0.90)
- Higher BMI categories are associated with lower sleep quality
- Occupational differences exist, with sales representatives reporting the lowest sleep quality
- Physical activity shows a modest positive correlation with sleep quality (r = 0.19)

---

## Contributors

- **Tara:** Visualizations, bootstrap analysis, data preparation
- **Roman:** GitHub repository, visualization finalization, overall commentary
- **Madhu:** Narrative refinement, visualization principles, presentation content

---

## License

This project is for educational purposes as part of a data analysis course.

---

## Additional Resources

- [Docker Documentation](https://docs.docker.com/)
- [Jupyter Notebook Documentation](https://jupyter-notebook.readthedocs.io/)
- [Dataset Source (Kaggle)](https://www.kaggle.com/datasets/uom190346a/sleep-health-and-lifestyle-dataset/)

---

## Questions or Issues?

If you encounter any problems:
1. Check the Troubleshooting section above
2. Verify all prerequisites are met
3. Ensure Docker is running (`docker ps` should not give an error)
