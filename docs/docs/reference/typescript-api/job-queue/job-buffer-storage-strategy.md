---
title: "JobBufferStorageStrategy"
weight: 10
date: 2023-07-20T13:56:15.674Z
showtoc: true
generated: true
---
<!-- This file was generated from the Vendure source. Do not modify. Instead, re-run the "docs:build" script -->
import MemberInfo from '@site/src/components/MemberInfo';
import GenerationInfo from '@site/src/components/GenerationInfo';
import MemberDescription from '@site/src/components/MemberDescription';


## JobBufferStorageStrategy

<GenerationInfo sourceFile="packages/core/src/job-queue/job-buffer/job-buffer-storage-strategy.ts" sourceLine="12" packageName="@vendure/core" since="1.3.0" />

This strategy defines where to store jobs that have been collected by a
<a href='/typescript-api/job-queue/job-buffer#jobbuffer'>JobBuffer</a>.

```ts title="Signature"
interface JobBufferStorageStrategy extends InjectableStrategy {
  add(bufferId: string, job: Job): Promise<Job>;
  bufferSize(bufferIds?: string[]): Promise<{ [bufferId: string]: number }>;
  flush(bufferIds?: string[]): Promise<{ [bufferId: string]: Job[] }>;
}
```
Extends

 * <a href='/typescript-api/common/injectable-strategy#injectablestrategy'>InjectableStrategy</a>



### add

<MemberInfo kind="method" type="(bufferId: string, job: <a href='/typescript-api/job-queue/job#job'>Job</a>) => Promise&#60;<a href='/typescript-api/job-queue/job#job'>Job</a>&#62;"   />

Persist a job to the storage medium. The storage format should
take into account the `bufferId` argument, as it is necessary to be
able to later retrieve jobs by that id.
### bufferSize

<MemberInfo kind="method" type="(bufferIds?: string[]) => Promise&#60;{ [bufferId: string]: number }&#62;"   />

Returns an object containing the number of buffered jobs arranged by bufferId.

Passing bufferIds limits the results to the specified bufferIds.
If the array is empty, sizes will be returned for _all_ bufferIds.

*Example*

```TypeScript
const sizes = await myJobBufferStrategy.bufferSize(['buffer-1', 'buffer-2']);

// sizes = { 'buffer-1': 12, 'buffer-2': 3 }
```
### flush

<MemberInfo kind="method" type="(bufferIds?: string[]) => Promise&#60;{ [bufferId: string]: <a href='/typescript-api/job-queue/job#job'>Job</a>[] }&#62;"   />

Clears all jobs from the storage medium which match the specified bufferIds (if the
array is empty, clear for _all_ bufferIds), and returns those jobs in an object
arranged by bufferId

*Example*

```TypeScript
const result = await myJobBufferStrategy.flush(['buffer-1', 'buffer-2']);

// result = {
//   'buffer-1': [Job, Job, Job, ...],
//   'buffer-2': [Job, Job, Job, ...],
// };
```