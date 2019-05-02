# Continuous integration / Continuous delivery / Continuous deployment
----------------------------------------------------------------------

Continuous integration is a practice where developers merge their changes back into the main branch as often as possible.
Developer changes are validated by creating a compilation and running automated tests against the build. When performing the process of continous iontefration, the that usually occurs when developers wait for the realease of a nes feature to merge their changes in the launch branch is avoided.

Continuous integration places great emphasis on automated testing to check whether a new feature is in trouble when new commits are being integrated into the core business.

*Continuous delivery* is an extension of continuous extension of continuous integration to ensure that you can quickly release new features to your customers in an agile and sustainable way. This means that in addition to automated testing, it has also automated the release process and you can deploy an application at any time by clicking a button.

In theory, with continuous delivery, it is possible to decide to make daily weekly, bi-weekly releases, or whatever is appropriate to business requirements. However, if we really want to reap the benefits of continuous delivery, we must send production features as early as possible to ensure delivery in small batches, which are easy to solve in case of a problem. It is important to remember that the final process of sending a version of an application for production depends on human intervention, as can be seen in the following diagram:

*Continuous deploy* goes one step beyond continuous delivery. With this practice, every change that passes through every step of your production pipeline is released to your customers. There is no human intervention, and only a failed test will prevent a new change from being implemented in production.

Continuous deployment is a great way to speed up the feedback loop for your customers. The delivery of new features does not have technically-structured planning as there is no release day anymore. Developers can focus on building software, and they see their work in production minutes after they finish development. Of course, reaching this release model requires stupendous automated testing coverage and a high degree of maturity from the development team.

In this model, unlike what happens with continuous integration, there is no human intervention to send new versions of the application for production, as can be seen in the following diagram

# The blue/green deployment pattern and Canary releases

The deploy blue/green pattern is very simple in its concept, and it is very efficient to send new versions of software for production. For the implementation of the deploy blue/green pattern, the API gateway, with microservices architecture, is of great help.

In a monolithic application, generally deployments are slower because every time a new version of the software is to be released, it must run the deployment of all the monolithics again. As the monolithic grows and becomes larger, it can become slow and problematic. With microservices, we can deploy individual components several times; it is usually faster and easier because of the size of the application thread itself being sent for production.

It is in the process of sending a new version of a microservice for production that the blue/green pattern is used. For example, if we have a microservice in version 1.0.0 and want to deploy version 1.0.1, an API gateway can know the location of both components and then provide an interface to switch traffic from the previous version to the new. The following diagram demonstrates very well the work of the API Gateway to make the change of versions using the blue/green pattern:

However, some deployments may entail a greater risk to the business of the application. In this scenario, a full version turn, as in the blue/green pattern, may not be the most appropriate. What would be interesting would be to run deploy, but direct requests to the new version of the software in a controlled way.

As a solution to this type of situation, we have the pattern called Canary release. The process is very similar to what is executed in blue/green patterns, and the difference is due to the gradual redirection of requests for the new version.

The requests control can be executed directly at the gateway. In this way, the impact in case of an error on the release of a new version will be much smaller. Take look at the following diagram for an overview of this process:

The progress of the number of requests redirected to the new version of the application will depend directly on how confident the development team is. This process is gradual and does not have a predeterminated time. The goal is to transfer 100% of the requests to the new version of the application.


