# Marc Marsiñach
engineering manager at pisos.com | lean & agile coach | software crafter | former CTO at fotocasa | ex computrabajo | bootstrapping wijobs.es

I enjoy coaching and helping companies on transforming their culture and organisation to get the most of their products and teams.

[LinkedIn](https://www.linkedin.com/in/marcmarsinach/)

[Twitter](https://twitter.com/marcmarsinach)

### Some of my skills:

`leading` `management` `mentoring` `coaching` `training` `one to one´s` `problem solving` `lean ux` `lean` `agile` `scrum` `kanban` `product management` `product roadmap` `software architecture` `microservices` `ddd` `cqrs` `software crafting` `tdd` `xp practices` `prototyiping` `a/b testing` `web development` `backend development` `graphic design` ...

### Languages
Spanish `native`

Catalan `native`

English `upper intermediate`

## Employment history

### Bootstrapping [Wijobs.es](https://www.wijobs.es)
`October 2019 - present`

`netcore` `entityframework` `mariadb` `elasticsearch` `kibana` `ml.net` `linux` `nginx` `ddd` `cqrs` `monolith`

This is my personal side-project, a job board where I have fun, learn new things and boost my creativity 🤟

### Engineering Manager at [Pisos.com](https://www.pisos.com)
`April 2016 - present`

`netcore` `aspnet.mvc` `sql server` `rabbitmq` `elasticsearch` `redis` `kibana` `ml.net` `microservices` `micro frontends` `ddd` `cqrs` `windows` `linux` `docker-swarm` `tdd` `nunit` `azure devops`

As an Engineering Manager I provide vision and expertise to develop leading-edge technologies from start to finish. I promote a culture of learning, collaboration, collective ownership and technical excellence. I encourage developers to know about the business and participate on product definition and prioritization, as well as to adopt best coding an deployment practices, review code frequently and put long-term quality at the front.

I ensure our products are build with the right methodology, technology and architecture choices. I mentor several cross-functional teams, guiding them with their Agile and Lean adoption, inspiring them to put customer needs at the front, getting user feedback frequently and taking decisions based on objective facts.

Together with the Team and the Product Manager we develop the product roadmap and the Hoshin plan and I assist the team to get our goals and take the best decisions.

### Technical Product Owner at [Computrabajo](https://www.computrabajo.com)
`February 2015 — March 2016`

`android` `retrofit` `asp.net web api` `mysql` `tdd` `nunit` `mockito`

Leading, coaching, mentoring and training a self-managed agile team with the goal of boosting our mobile products. Our process is based on Lean principles, identifying user problems, verifying assumptions and building solutions with a fast iterative process.

### CTO at [Fotocasa](https://www.fotocasa.es)
`November 2005 — January 2015`

`asp.net mvc` `netframework` `lucene` `sqlserver` `memcached` `redis` `jenkins` `sonarqube` `umbraco` `tdd` `specflow` `nunit`

Leading the fotocasa engineering team organized across several cross-functional teams running scrum or kanban.

Working with the development teams for defining the software architecture patterns with consistent high availability, scale and security. Providing coaching and training to promote a culture of good coding practices, deploy and test automation and coding standards.

Assisting in the product definition providing the technical vision from the dev team.

### Software developer at Anuntis Segundamano
`June 2000 — November 2005`

### Show me the code!

A typical simplified command handler:

```csharp
using (var unitOfwork = unitOfWorkFactory.CreateFor<Job>())
{
    var repository = unitOfwork.GetRepository<Job>();

    var job = await repository.FindAsync(jobId);

    if (job?.Id == default)
        throw new JobNotFoundException();

    job.UpdateFrom(command.Job);

    await unitOfwork.SaveChangesAsync();
    
    await bus.RaiseEvents(job);
}
```

An integration test

```csharp
[Test]
public async Task CreateJobController_should_create_a_new_job()
{
    using (var scope = ServiceProvider.CreateScope())
    {
        // Arrange
        var bus = scope.ServiceProvider.GetRequiredService<IBus>();
        var logger = scope.ServiceProvider.GetRequiredService<ILogger<JobController>>();
        var correlationId = Guid.NewGuid();
        var controller = new JobController(bus, logger);

        var job = new JobDTO()
        {
            Title = "My job offer",
            ...
        };

        var request = new PostJobRequest(
            job,
            companyId,
            userId
            );

        // Act
        ActionResult response = await controller.CreateAsync(request, correlationId);

        // Assert
        Assert.That(response, Is.InstanceOf(typeof(OkObjectResult)));
        Assert.That...
        Assert.That...
    }
}
```

A unit test

```csharp
[Test]
public async Task SaveJobCommandHandler_should_get_a_job_entity_from_repository_given_a_valid_job_id()
{
    // Arrange
    var correlationId = Guid.NewGuid();
    var jobRepository = new Mock<IJobRepository>();
    var logger = new Mock<ILogger>();
    var job = new Mock<Job>();

    job.SetupProperty(m => m.Id, JOB_ID);
            
    var command = new SaveJobCommand(correlationId, job.Object);
    var handler = new SaveJobCommandHandler(jobRepository.Object, logger.Object);

    // Act
    await handler.Handle(command);

    // Assert
    jobRepository.Verify(r => r.FindAsync(JOB_ID), Times.Once);
}
```
