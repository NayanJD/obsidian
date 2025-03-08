
I am currently using Notion for [PARA](https://youtu.be/T6Mfl1OywM8?si=oPHQLQkyFYfAODs6)  (Project, Areas, Resource, Archive) otherwise known as "Second Brain". Ironically, obsidian is also a "Second Brain" tool but mainly for knowledge centre. Hence, I am using notion to mange the Project, Areas and Archive section, ie. for the task management section. For the resource section, I am using obsidian.

[This](https://youtu.be/HvSBfnQmEiU?si=damMDmL_H5I7CxtG) is the video I used to create my [Second Brain](https://www.notion.so/Second-Brain-1b088e986af18016a3aee33a52349994?pvs=4) on notion. I am not adding any notes for this video since it would be redundant (hopefully, this video lives forever).

[My Notion Face](https://faces.notion.com/share?face=s1e25m105n27h164a3b23) 


### Notion Database

A notion database is a set of items which are none other than pages with some attributes. We can create a database and add a `Relation` attribute to it to create a 1-to-1 mapping to another database. 

To create a summary or a computed value of child database items in a parent one, we can add a `Rollup` property which has some handy aggregates like sum, count etc.

We can also add a `Formula` property to a item in a database which has useful functions which can work upon other properties. I have used this to compute the time taken (end time - start time) for a session in pomodoro page.


### Todo

- [ ] Create (or host) a custom pomodoro website which calls notion api using integration token and log a session in the pomodoro database.
- [ ] Explore https://github.com/kevinschoon/pomo