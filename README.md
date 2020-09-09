# MicroServices

## Setup of the application:

**Prerequisites:** [Java 11](https://sdkman.io/sdks#java) and an internet connection.

To install this example, run the following commands:

```bash
git clone https://github.com/Rashmi206/Microcredentials.git
```

The `api-gateway` and `car-service` projects are already pre-configured to be locked down with OAuth 2.0 and Okta. That means if you try to run them, you won't be able to login until you create an account, and an application in it.

### Create a Web Application in Okta

Log in to your Okta Developer account (or [sign up](https://developer.okta.com/signup/) if you don't have an account).

1. From the **Applications** page, choose **Add Application**.
2. On the Create New Application page, select **Web**.
3. Give your app a memorable name, add `http://localhost:8080/login/oauth2/code/okta` as a Login redirect URI, select **Refresh Token** (in addition to **Authorization Code**), and click **Done**.

Copy the issuer (found under **API** > **Authorization Servers**), client ID, and client secret into the `application.properties` of the `api-gateway` and `car-service` projects.

```properties
okta.oauth2.issuer=https://{yourOktaDomain}/oauth2/default
okta.oauth2.client-id=$clientId
okta.oauth2.client-secret=$clientSecret
```

Then, run all the projects with `mvn spring-boot:run` in separate terminal windows. You should be able to navigate to `http://localhost:8761` and see the apps have been registered with Eureka.

Then, navigate to `http://localhost:8080/cool-cars` in your browser, log in with Okta, and see the resulting JSON.

## Devops Setup Instructions

- Created Jenkinsfile and checked in to Github.
- Automatically triggers the Jenkins pipeline whenever code is pushed to Github.
- Through Jenkins the code is pulled from Github repository, build and tests are run.
- Docker Images are created and pushed to Dockerhub.
- Images are being pulled from Dockerhub and is being deployed in docker containers.

## Flowchart
![alt text](Flowchart.png?raw=true)