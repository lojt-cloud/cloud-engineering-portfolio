## Week 1 — Cloud Fundamentals (Days 3–5)

## Day 3 — S3 storage (labs)

After covering S3 theory the day before, Thursday was about actually
building with it. Two labs back to back.

First lab: created an S3 bucket from scratch, uploaded files via both
the console and CLI, set up folder structure (images/, documents/,
backups/), configured storage classes (Standard, Standard-IA,
Intelligent-Tiering), enabled versioning and SSE-S3 encryption, and
practised sync operations. The CLI syntax for downloads and deletes
still needs repetition, but the logic behind storage classes made sense
Well, it's essentially a cost vs. retrieval speed tradeoff depending
on how often you actually need the data.

Second lab: hosted a static website on S3. Created the bucket, disabled
public access block, enabled static website hosting, applied a bucket
policy to allow public reads, and uploaded HTML/CSS files. Got the site
loading live at the S3 endpoint URL and the custom 404 error page
working correctly.

Key thing that stuck: S3 buckets are private by default for good reason.
Enabling static hosting gives you an endpoint, but without the bucket
policy explicitly allowing s3:GetObject for everyone, nothing actually
loads. Two separate switches — easy to miss one.

One CLI gap: I ended up enabling website hosting through the console
instead of CLI because I wasn't confident enough in the syntax yet.
Something to go back and practice.

## Day 4 — Linux CLI essentials

Deep dive into Linux. Started with navigation and file operations —
nothing surprising given the prework, then moved into the tools that
actually make Linux useful for cloud work: grep, awk, sed, pipes, and
redirects.

grep with flags (-n for line numbers, -c for count, -o for extract
pattern) is genuinely useful for log analysis. The CloudTrail JSON
parsing exercise showed how directly this transfers to real AWS work —
same commands, real data format.

File permissions finally made sense. Understanding the r/w/x math rather
than just copying chmod numbers felt like an important shift. Applied
chmod 600 to a config file holding a database password — same
least-privilege logic as IAM, just at the OS level.

One problem I hit: tried to create a log file at app/logs/application.log
and got "No such file or directory". Took about 3 minutes to figure out
the parent directory didn't exist yet. Fixed with mkdir -p app/logs first.
Small thing, but a good reminder that file paths have to exist before
you write to them. 
The reason for this is that I started to work in a different
directory from the previous task and got confused.

The process management section (ps, jobs, kill, bg) made sense
conceptually, but hasn't felt real yet — I haven't had to actually use it
for a running service. That'll come.

## Day 5 — Linux for cloud engineering (advanced labs)

This was a big jump. Right after getting comfortable with grep and basic
piping, the labs moved straight into awk, sed, cut, jq, and full shell
scripting. Two labs, roughly 8.5 hours total across the day.

The first lab (Linux Command Line Essentials, ~3 hours 10 minutes) was built
on the previous day's tools — server log analysis with awk (counting
requests per IP, averaging response sizes, filtering 4xx/5xx errors),
config file transformations with sed, CSV column extraction with cut,
and AWS JSON parsing with jq. The jq section was new territory — the
nesting in AWS CLI output (Reservations → Instances → Tags) requires
chained filters that take some getting used to.

The second lab (Linux for Cloud Engineering, ~5 hours 20 minutes) was
where it got genuinely difficult. Rather than isolated commands, we had
to implement tools into pre-written scripts and extend them with new
features — rollback logic, email simulation, smoke tests, production
approval gates. A lot of syntax I hadn't seen before, and unlike earlier
in the week when I could look something up and understand it, here I
needed AI to explain what parts of the given scripts were doing before I
could even figure out where to add my own code.

Managed to get through all the tasks, and actually spotted a bug in the
base cost report.sh script: the monthly costs were supposed to be listed in
descending order, but weren't. Knew sort was the right tool, but couldn't
work out the exact placement — the $ symbol in the formatted output was
breaking the numeric sort. Used AI to work through the fix: separate the
sort step from the formatting step, sort plain numbers first, then
reformat with printf afterwards.

Getting it working was satisfying. But this lab probably needed to be
two separate sessions.

## Ongoing — Git workflow

The labs this week were too large to stick to the branching routine
properly. Core learning took priority, and most commits went straight to
main. This is a habit to rebuild next week when the pace settles — small
commits on a branch, not one big push at the end.

## What I'd do differently

The second Friday lab (Linux for Cloud Engineering) needed to be split
into two. Five and a half hours on material that was mostly new syntax,
with scripts that had unknown parts throughout, was too much to absorb
in one go. The right approach would have been to work through one script
fully, understand it, then move to the next — not try to complete all
nine tasks in sequence.

Also: more deliberate CLI practice outside the labs. The commands make
sense when I'm following a task, but they're not automatic yet.

## Up next — Day 5 theory + Week 2 start

Covered the theory for AWS Billing Dashboard and Cost Optimisation Tools
on Friday afternoon. Monday picks up with the hands-on: cost alerts,
billing alarms, and anomaly detection in AWS.
