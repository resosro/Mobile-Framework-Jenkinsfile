pipeline{
    // Does agent {label 'Selenium'} work here? or does it have to be 
    // node {label 'Selenium '}
    agent {label 'QuantumX'}

    parameters{
        choice(name: "mobile_app", choices: ['Earth Mobile', "ArcGIS Mobile"], description: 'Select which mobile app to run')
        choice(name: "phone_version", choices: ["Pixel 4"], description: "Select which one to be used")
        choice(name: "android_os", choices: ["11.0"], description: "Select the Android OS")
        choice(name: "portal_os", choices: ["Lnx","Windows"], description: "Select the portal OS")
        choice(name: "portal_version", choices: ["11.2"], description: "Select the portal version")
        choice(name: "security_type", choices: ["BI"], description: "Select the security type")
    }

    environment {
        PWD = pwd()
    }

    stages{
        stage("Checkout 1"){
    steps{
        dir('Module1') {
                git branch: 'main', credentialsId: 'c673d917-5c3d-4d1e-8e15-4815077fc9fb', url: 'https://github.com/resosro/Mobile-Framework-Pipeline.git'                
            }
            pwsh "${env.PWD}//Module1//ps-scripts//build.ps1"
        }
}
    
        stage("Checkout 2"){
            steps{
                 dir('Module2') {
                    git branch: 'main', credentialsId: 'c673d917-5c3d-4d1e-8e15-4815077fc9fb', url: 'https://github.com/resosro/ArcGIS-Earth-Mobile.git'}
            }
            pwsh "${env.PWD}//Module1//ps-scripts//build.ps1"

        }
        
        

        stage("Clean"){
            steps{
                bat "${PWD}\\Powershell-Scripts\\clean.ps1"

            
        }
    }
}
}
    