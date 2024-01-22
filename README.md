
# Python project to standalone executable

packaging the project is not mandatory. However, organizing your code into a project structure can make it more maintainable and easier to collaborate on. If you plan to share your Streamlit app with others or deploy it to a cloud platform, having a well-organized project structure can be beneficial.

## step 1 - Package the Python project

Creating the package files:-

You will now add files that are used to prepare the project for distribution. When you’re done, the project structure will look like this

iris_classifier_project/
├── src/
│   ├── __init__.py
│   ├── app.py
│   ├── model.py
│   └── data.py
├── requirements.txt
├── setup.py
├── pyproject.toml
├── LICENSE.txt
└── README.txt



## Packaging Python Projects

[Documentation](https://packaging.python.org/en/latest/tutorials/packaging-projects/)


## 1st Approach- Converting Streamlit application to exe file using nativefier Approach

## nativefier

[Documentation](https://ploomber.io/blog/streamlit_exe/)

Streamlit is an open souce framework for converting data scripts into shareable web applications. It allows data scientists and machine learning engineers to build intuitive interfaces without having to know web development.

The main motivation behind this is that users should be able to bundle the Streamlit application and all of its dependencies into a single package. This bundled package can be easily shared with other users who do not have Streamlit or even Python installed in their machines.

#### 1 . lets use the streamlit application we created for the iris_classifer_project:


from iris_classifier_project import main

if __name__ == "__main__":
    main()
    
#### 2 . This application can be run from the terminal using the below command:

streamlit run streamlit_app.py

## Nativefier Approach
Nativefier is a command-line tool that easily creates a desktop app for any web site with minimal configuration. Apps are wrapped by Electron in an OS executable (.app, .exe, etc.) for use on Windows, OSX and Linux. Note that converting Streamlit applications using Nativefier requires users to deploy the application to Streamlit Share(https://share.streamlit.io/)

Streamlit Share is a platform provided by Streamlit for deploying and sharing Streamlit apps without the need for a separate hosting service. Streamlit itself is an open-source Python library for creating web applications with minimal effort. It's particularly popular for creating interactive and data-driven dashboards with Python scripts.

### Install nativefier by running the below command:

npm install -g nativefier
### Now convert your Streamlit application like so:

nativefier --name '<app.exe name>' '<streamlit sharing website url>' --platform <'windows' or 'mac' or 'linux'>

for the iris_classifer_project the command is - 
nativefier --name streamlit_app --platform windows

This will create the exe file in the current directory.


## 2nd Approach- Converting Streamlit application to exe file using pyinstaller 

PyInstaller is a program that converts (packages) Python programs into standalone executables. This is useful when you want to distribute a Python application as a single executable file, making it easier for users to run your program without needing to install Python and its dependencies separately.

pyinstaller- https://pyinstaller.org/en/stable/

### 1. Initialize Python Project

python -m venv venv

activate the envirnoment

### 2. Install the required dependencies and Streamlit:

pip install -r requirements.txt

### 3. Ensure your Streamlit app runs successfully:

streamlit run streamlit_app.py

### 4. Install PyInstaller

pip install pyinstaller

### 5.  Create Executable:Run the following command to create a standalone executable:

pyinstaller --onefile streamlit_app.py

This will create a dist folder containing your standalone executable.

The --onefile option in PyInstaller is used to create a single, standalone executable file. When you use --onefile, PyInstaller bundles all the necessary dependencies and the main script into a single executable file.

