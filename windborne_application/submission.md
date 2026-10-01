# Software Engineer, Machine Learning Systems — Application Challenge

## 1. Tell us about a problem you couldn’t leave alone. What did you build to fix it?

At OPCL, I kept coming back to one problem: equipment warnings were arriving too late to be very useful. Existing SCADA thresholds caught only 46% of the mechanical and thermal stoppages we studied, and the median warning was about 12 minutes.

I wanted to know whether the sensor data already contained earlier signals that the fixed thresholds were missing. I built a two-stage early-warning system. The first stage modeled expected sensor behavior for each unit based on operating conditions. I then used the residuals, rolling trends, alarm counts, and operating context as features for a LightGBM classifier.

On 37 qualifying events, recall improved from 46% to 84%, while median warning time increased from 12 minutes to 6.5 hours.

What interested me most was not just improving a metric. It was learning how to turn messy physical-system data into something that could provide earlier, more useful signals without flooding operators with alerts.

## 2. Tell us about a time you had to understand an unfamiliar system that wasn’t behaving as expected. How did you get to the bottom of it?

While building AgentShield, I needed to compare safety evaluations across different runs. At first, a simple before-and-after score was not enough. Some test cases could be compared directly, while others had changed enough that treating them as the same case would give misleading regression results.

I traced the workflow end to end: attack loading, LangGraph execution, retrieval, evaluation, persistence, and reporting. Instead of trying to fix the final report, I worked backward and made the identity of each test case explicit.

I introduced stable, versioned attack IDs and defined comparison states such as improved, regressed, unchanged, new, and not comparable. I then built deterministic regression tests around that behavior.

That gave me a benchmark where all 8 aligned cases moved from fail to pass with zero regressions, and the repository finished with 90 passing tests.

The main lesson was that when a system looks wrong at the output, I try to understand where its assumptions first become wrong rather than patching the final symptom.

## 3. Describe a real coding task where AI tools helped you move faster. Where did you have to step in and think for yourself?

I use AI coding tools a lot when I am working in an unfamiliar part of a codebase. AgentShield is a good example. I was combining LangGraph state management, MCP-based attack delivery, FastAPI, RAG, SQLite checkpoints, and an evaluation pipeline.

AI tools helped me understand APIs faster, sketch implementations, generate first-pass tests, and explore alternatives without spending as much time searching documentation.

The part I could not hand off was deciding what the system should actually mean. For example, I had to decide when two evaluation cases were comparable, what counted as a regression, how failures should propagate, and which behavior needed deterministic tests. An implementation can be syntactically correct while still encoding the wrong assumptions.

My rule is that AI can help me reach a candidate solution quickly, but I still trace the data flow, read the generated code, test edge cases, and make the final architecture and failure-handling decisions myself.

## 4. Describe the extent to which you have experience with production systems.

My experience is a mix of operational systems and production-adjacent software, but I would not claim that I have already owned a 24/7 ML inference service at the scale WindBorne operates.

At OPCL, I worked with real SCADA, generation, and outage data from an operating power plant. My forecasting work also included a live shadow run, so I had to think about how models behaved on incoming operational data rather than only on a static training set.

At Anthem Nation, I worked on beta/UAT systems that connected AWS services, APIs, human review, and Snowflake data pipelines. I used S3, Lambda, API Gateway, CloudWatch, Snowpipe, Streams, and Tasks, including logging and failure visibility.

I have also built systems with automated testing, persistence, APIs, and monitoring-oriented workflows.

What I am looking for next is exactly the step this role offers: deeper ownership of software that must keep running, recover from failures, and make its state understandable when something goes wrong.

## 5. How many years of relevant experience do you have?

About 2.5 years of relevant hands-on experience across data science, machine learning, data pipelines, and software systems, excluding overlapping roles.
