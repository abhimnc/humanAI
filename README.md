# HumanAI Test Submission

Hi guys! Welcome to my repository for Google Summer of Code 2025 Test - AI-Enabled Choreography: Dance Beyond Music. This project focuses on submission of test provided by HumanAI.

For a hands-on experience, dive into my Google Colab Notebook which provides an interactive demonstration of the network.


Problem Addressed

This project aims at solving two coding problems provided in test document.
It outlines a approach to Animate some dance data and Train a multimodal model of dance & text.



Solution Approach
    
    Understand key relationships between parts of the body of each dancer
    Animate data using given references in test documents
    Create dataset by running web app locally of repo refered in test document (https://github.com/geometric-intelligence/pirounet) for 1% of dataset(around 70 labelling will be done, since there are around 6803 dataset)
    Devise a way to apply these labels automatically to similar-looking sequences in the rest of the data.
    Use contrastive learning to embed short fixed-length dance phrases  and a natural language description of those phrases into a single shared embedding space

The comprehensive solution plan involves:




Key Deliverables

    Construction a 3D plotting function that allows to visualize animated dance sequences in the data in for sequences of length t timesteps. 
    Create a dataset of point-cloud data corresponding to extracted motion capture poses given in dataset example
    Use this motion capture data to train a neural network that uses contrastive learning to embed short fixed-length dance phrases
    Create a natural language description of those phrases into a single shared embedding space.


Detailed Solution

Data preparation

Since, dataset is taken from repo - https://github.com/mariel-pettee/choreo-graph/tree/main. I reused the code to run in colab to visualize dataset.

Overflow flow code:
```
main()
│
├── load_data(pattern)                 # Loads and processes .npy motion capture data
│   ├── Normalizes data
│   ├── Computes velocity
│   └── Stacks positions + velocities
│
├── animate_stick(...)                # Creates stick-figure animation from motion sequence
│   ├── get_line_segments(...)        # Computes line segments for joints (skeleton & cloud)
│   └── put_lines(...)                # Adds 3D line segments to the plot (skeleton & cloud)
│
├── display(HTML(anim.to_jshtml()))   # Displays the animation in a Jupyter/Colab notebook
│
└── (Optionally)
    └── save_animation(...)           # Saves animation as a video (MP4) and offers download
    
Other Supporting Functions (Used Separately or Conditionally)
create_sample_data()         # Generates synthetic walking motion data (for testing)
upload_npy_files()           # Colab interface to upload .npy files (if needed)
```


Model Structure
