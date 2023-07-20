---
title: "InMemoryJobQueueStrategy"
weight: 10
date: 2023-07-20T13:56:15.656Z
showtoc: true
generated: true
---
<!-- This file was generated from the Vendure source. Do not modify. Instead, re-run the "docs:build" script -->
import MemberInfo from '@site/src/components/MemberInfo';
import GenerationInfo from '@site/src/components/GenerationInfo';
import MemberDescription from '@site/src/components/MemberDescription';


## InMemoryJobQueueStrategy

<GenerationInfo sourceFile="packages/core/src/job-queue/in-memory-job-queue-strategy.ts" sourceLine="42" packageName="@vendure/core" />

An in-memory <a href='/typescript-api/job-queue/job-queue-strategy#jobqueuestrategy'>JobQueueStrategy</a>. This is the default strategy if not using a dedicated
JobQueue plugin (e.g. <a href='/typescript-api/job-queue/default-job-queue-plugin#defaultjobqueueplugin'>DefaultJobQueuePlugin</a>). Not recommended for production, since
the queue will be cleared when the server stops, and can only be used when the JobQueueService is
started from the main server process:

*Example*

```TypeScript
bootstrap(config)
  .then(app => app.get(JobQueueService).start());
```

Attempting to use this strategy when running the worker in a separate process (using `bootstrapWorker()`)
will result in an error on startup.

Completed jobs will be evicted from the store every 2 hours to prevent a memory leak.

```ts title="Signature"
class InMemoryJobQueueStrategy extends PollingJobQueueStrategy implements InspectableJobQueueStrategy {
  protected protected jobs = new Map<ID, Job>();
  protected protected unsettledJobs: { [queueName: string]: Array<{ job: Job; updatedAt: Date }> } = {};
  init(injector: Injector) => ;
  destroy() => ;
  async add(job: Job<Data>) => Promise<Job<Data>>;
  async findOne(id: ID) => Promise<Job | undefined>;
  async findMany(options?: JobListOptions) => Promise<PaginatedList<Job>>;
  async findManyById(ids: ID[]) => Promise<Job[]>;
  async next(queueName: string, waitingJobs: Job[] = []) => Promise<Job | undefined>;
  async update(job: Job) => Promise<void>;
  async removeSettledJobs(queueNames: string[] = [], olderThan?: Date) => Promise<number>;
}
```
Extends

 * <a href='/typescript-api/job-queue/polling-job-queue-strategy#pollingjobqueuestrategy'>PollingJobQueueStrategy</a>


Implements

 * <a href='/typescript-api/job-queue/inspectable-job-queue-strategy#inspectablejobqueuestrategy'>InspectableJobQueueStrategy</a>



### jobs

<MemberInfo kind="property" type=""   />


### unsettledJobs

<MemberInfo kind="property" type="{ [queueName: string]: Array&#60;{ job: <a href='/typescript-api/job-queue/job#job'>Job</a>; updatedAt: Date }&#62; }"   />


### init

<MemberInfo kind="method" type="(injector: <a href='/typescript-api/common/injector#injector'>Injector</a>) => "   />


### destroy

<MemberInfo kind="method" type="() => "   />


### add

<MemberInfo kind="method" type="(job: <a href='/typescript-api/job-queue/job#job'>Job</a>&#60;Data&#62;) => Promise&#60;<a href='/typescript-api/job-queue/job#job'>Job</a>&#60;Data&#62;&#62;"   />


### findOne

<MemberInfo kind="method" type="(id: <a href='/typescript-api/common/id#id'>ID</a>) => Promise&#60;<a href='/typescript-api/job-queue/job#job'>Job</a> | undefined&#62;"   />


### findMany

<MemberInfo kind="method" type="(options?: JobListOptions) => Promise&#60;<a href='/typescript-api/common/paginated-list#paginatedlist'>PaginatedList</a>&#60;<a href='/typescript-api/job-queue/job#job'>Job</a>&#62;&#62;"   />


### findManyById

<MemberInfo kind="method" type="(ids: <a href='/typescript-api/common/id#id'>ID</a>[]) => Promise&#60;<a href='/typescript-api/job-queue/job#job'>Job</a>[]&#62;"   />


### next

<MemberInfo kind="method" type="(queueName: string, waitingJobs: <a href='/typescript-api/job-queue/job#job'>Job</a>[] = []) => Promise&#60;<a href='/typescript-api/job-queue/job#job'>Job</a> | undefined&#62;"   />


### update

<MemberInfo kind="method" type="(job: <a href='/typescript-api/job-queue/job#job'>Job</a>) => Promise&#60;void&#62;"   />


### removeSettledJobs

<MemberInfo kind="method" type="(queueNames: string[] = [], olderThan?: Date) => Promise&#60;number&#62;"   />

