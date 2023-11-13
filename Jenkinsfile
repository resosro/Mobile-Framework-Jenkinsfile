pipeline{
    // Does agent {label 'Selenium'} work here? or does it have to be 
    // node {label 'Selenium '}
    agent {label 'RAppsDesktop11'}

    parameters{
        choice(name: "mobile_app", choices: ['Earth Mobile', "ArcGIS Mobile"], description: 'Select which mobile app to run')
        choice(name: "phone_version", choices: ["Pixel 4"], description: "Select which one to be used")
        choice(name: "android_os", choices: ["11.0"], description: "Select the Android OS")
        choice(name: "portal_os", choices: ["Lnx","Windows"], description: "Select the portal OS")
        choice(name: "portal_version", choices: ["11.2"], description: "Select the portal version")
        choice(name: "security_type", choices: ["BI"], description: "Select the security type")


    }

    stages{
        stage("Build"){
            steps{
                git branch: 'main', credentialsId: 'c673d917-5c3d-4d1e-8e15-4815077fc9fb', url: 'https://github.com/resosro/Mobile-Framework-Jenkinsfile'                echo "branch pulled"
                bat "ls"

                bat "cd .\\scripts ls"
                echo "${PWD}"
                bat "${PWD}\\Insights-Desktop-Pipeline\\scripts\\build.ps1"
            }
        }
        stage("Test"){
            steps{
                git branch: 'main', credentialsId: 'd28f4340-67ba-48ac-a47d-810f37cf684c', url: 'https://devtopia.esri.com/Release/Insights-DesktopAutomation'
                bat "${PWD}\\Powershell-Scripts\\test.ps1"
            }

        }

        stage("Clean"){
            steps{
                bat "${PWD}\\Powershell-Scripts\\clean.ps1"

            }
        }
    }
}
