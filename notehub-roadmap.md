Note taking App

MVP
Problem: I need a way to manage and share my notes with other users through servers 
Features: 
  - [x] user can login to access app 
  - [x] user can create a single profile with userName, imageUrl, and bio
    feature flow: user logs in -> check for existing profile connected to user in home page -> if exists, load. if not -> profile creation modal -> fields: userId (from clerk), name, bio?, imageUrl? -> create -> direct to home page with notes
    - [x] get userId from clerk
    - [x] find profile connected to user by userId
    - [x] if profile exists, return. if not, create new profile
    - [x] append a random 4 digits uuid or cuid to name field
  - [x] user can create posts. this will be text editor for note taking
  - [x] user can display list of posts
  - [x] user can edit posts
  - [x] user can delete posts

  - [x] user can create servers
    - [x] /server/create page
    - [x] form with create: profileId, name, members: {create: profileId, role: MemberRole.ADMIN}
    - [x] add list of servers to side nav bar
        - find all servers the profile is a member of. 
        - db.server.findMany({
		where: {
			members: {some: {profileId: profile.id}}
		}
            })
    - [x] view server page [serverId] 

 - [x] display notes related to server or add note button
 - [x] move edit note btn to view note
 - [x] user can post their notes to any server from their collection while on
   server view
      - [x] open modal that lists all notes
      - [x] click on individual note will call server action to add serverId to
        note
      - [x] close modal
      - [x] revalidate server page
 - [x] user can toggle home, profile, create, server views
 - [] user can invite other users to server
 - [x] fix UI for login and signup pages
 - [] fix UI for entire app (layout, theme)
 - [] replace alerts with toasts
 - [] handle prisma errors
 - [] e2e tests
 - [] unit/integration tests

Roadmap: 
- make an app that students can share notes with each other. 
- something like google docs but optimized for note taking
- key features: 
  - [] users have a board of notes for themselves. 
  - [] users have a robust note taking system in app 
    - rich text editor
    - focus on efficiency like vim
    - typing and writing/drawing options
    - audio recording options to post lectures
    - markup pdfs, lecture slides, and forms
    - scan documents to create pdfs

nice to have: 
  - [] user can create servers to post notes to
  - [] user can invite other users to the server
  - [] user can save posts as drafts
  - [] user can click on drafts to edit and publish
  - [] users can chat with other users in each general server. (chat sidebar like skype)
  - [] users can chat with other users for each note posted 
  - [] users can multiselect in 'add notes to server' feature and add multiple
    notes to a server with one request
  - [] optimistic updates for server mutations

optimize: 
  - [] replace Clerk with Next Auth. Clerk makes every page dynamic

