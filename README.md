# Kontentblocks

Kontentblocks (KB) is kind of a content builder plugin, but not based on the idea of endless possibilities.  
Build around the common workflow of agency/client projects, where design constraints are a matter

**Developers** will get a toolkit/framework to quickly build flexible content elements (modules) which are hooked onto predefined areas in the template files.

**Users** will be able to easily manage and create their content as it was designed/developed – with a reduced chance of breaking things.  

###Core Features

####Fields API

A powerful integrated API for building input forms for modules or custom data panels for post-types and/or admin menus.
Fields can be set up on context specific conditions or the chosen module view

####Twig template engine

Twig is fully integrated into the module concept, usage is optional though. If configured, users can chose from available module views, Fields can depend on those views...well, quite powerful stuff, reusable and seperated code...

####Frontend & inline editing

Input forms of modules are always accessible on the frontend through a modal.
If you chose to, there is true **inline editing** support for text and image related field types yet. (...this part will receive much more attention in the future and is currently in a proof-of-concept phase)

####Code driven

There is very few clicky-di-click involved and most things must be coded. It's a developers toolkit, users should only **use** whatever you've built for them.

####Minimal invasive

The plugin / the idea implies a certain workflow but it does not force you to do things in one specific way. It does not make any assumptions about your design, build process or favorite css framework. It does not create meta boxes, it will not ask you for a pro version or donation and there are no admin pointers involved. It will add one additional menu item..(well I should make this optional). No shop, no usage limitations, no commercial intentions, promised.

###Things, you might ask

####Can it be used with any theme?

Yes and no. Template files must be modified to integrate the plugin. No big changes, but necessary.  
It's really not plug n' play. So you should have some skills in coding.

#### What modules / content elements are included?

None.How should I know what you or your client really need for the next awesome project? But it's quite easy to build them, really.   
I like the idea of having some kind of exchange in the future, though.

#### How is the data stored?

Here comes the downer. Module data, by default, is stored as serialized arrays in the post meta table.

**Good thing:** It won't affect any other plugins which rely on the post_content or if you extend an existing website with the plugin.   
**Bad thing:** serialized arrays.. 

Technical, there are ways to map the html output of modules/areas to **post_content**, to keep WordPress core concepts intact. This feature is disabled by default and needs a good plan and some configuration.

It's possible to use a custom data handler as well, which makes sense if you want to map data to elasticsearch or a MongoDB for example. If you wonder why you should do something like that, you really won't need that possibilty at all...but it's there.

#### What happens to my content if I switch themes?

To be clear about that: the whole development and usage of the plugin during the last three years is not build around the WordPress way resp. switching themes every X weeks ( like many so-called premium, commercial plugins and themes are not as well ).  
It depends on the setup and content strategy how much content is preserved or visually lost when disabling the plugin or using a theme which is not prepared.  

The raw data is not deleted unless somebody descides to delete it on purpose – but there won't be a shortcode massacre left as well...

#### Multilanguage support?

If you like it or not: WPML will support this plugin out of the box.
I've never looked into other plugins, because I simply don't own a copy of them.

**If you like the idea and you are great coder, designer, thinker or critic: feel free to get in touch, there is still much to do and I'm always open to learn new thing, hear different thoughts and opinions**  

###Bugs & Issues
Yeah, sure!  
Most "bugs" you might encounter are UI/UX specific inconsistencies.  
Thoses little details which cost time to do right, time which hasn't been found yet. Time, which would make this idea awesome instead of just good.
