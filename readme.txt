=== Customize Posts ===
Contributors:      xwp, westonruter, valendesigns
Tags:              customizer, customize, posts, preview, featured-image, page-template
Requires at least: 4.5
Tested up to:      4.6
Stable tag:        0.7.0
License:           GPLv2 or later
License URI:       http://www.gnu.org/licenses/gpl-2.0.html

Edit posts and postmeta in the Customizer. Stop editing your posts/postmeta blind!

== Description ==

*This is a feature plugin intended to implement [#34923](https://core.trac.wordpress.org/ticket/34923): Introduce basic content authorship in the Customizer.*

The goal for this plugin is to be able to expose the editing of posts and pages in the Customizer, allowing you to edit post data and postmeta for any number of posts, and preview the changes before saving them for others to see. This plugin was birthed out of the Widget Customizer feature-as-plugin project which was merged into WordPress Core: as widgets (in 3.9) and nav menus (4.3) can now be managed in the Customizer, so too should posts and pages be editable in the Customizer as well.

Did you know that **changing the featured image actually makes the change live even before you save the post**? This is very surprising/unexpected behavior. The only way to truly preview a change to a featured image is to use something like Customize Posts.

Likewise, did you know that **changing a page template cannot be previewed from the post editor?** When you change the selected page template, the change will not show up when you preview the page (see [#11049](https://core.trac.wordpress.org/ticket/11049)). However, in Customize Posts you *can* preview changes to the page template just by changing the dropdown selection, and then you can see what your page would look like with the new template after the preview refreshes.

Most other changes to metaboxes containing data that gets saved to custom fields (postmeta) also get written when clicking the Preview button. The Customize Posts plugin provides a framework to edit postmeta in the Customizer with a live preview of the changes. (Fixing this underlying issue of incorrectly persisting postmeta when doing a preview is captured in [#20299](https://core.trac.wordpress.org/ticket/20299).)

As much as possible, the previewing of changes in Customize Posts utilizes the [selective refresh](https://make.wordpress.org/core/2016/02/16/selective-refresh-in-the-customizer/) capabilities introduced in WordPress 4.5. Not only does this mean it is faster to preview changes to posts and postmeta, but it also allows you to shift-click on an element to focus on the corresponding control in the Customizer pane. For example you can shift-click on the post title in the preview to focus on the post title control's input field, or shift-click on a featured image to focus on the control's button to open the media library.

**Development of this plugin is done [on GitHub](https://github.com/xwp/wp-customize-posts). Pull requests welcome. Please see [issues](https://github.com/xwp/wp-customize-posts/issues) reported there before going to the [plugin forum](https://wordpress.org/support/plugin/customize-posts).**

(This **Customize Posts** plugin is not to be confused with 10up's [**Post Customizer**](https://github.com/10up/Post-Customizer).)

= Demo Videos =

The following are listed in reverse chronological order. The first, more recent videos, show more polish.

[2016-04-28] New features in 0.5.0.

[youtube https://www.youtube.com/watch?v=2NXh-1_eUqI]

[2016-03-28] Previewing post from Post Edit screen.

[youtube https://www.youtube.com/watch?v=Q62nav1k4gY]

[2016-03-05] Opening a draft post in the Customizer to preview title wrapping.

[youtube https://www.youtube.com/watch?v=sXu2pA42J88]

[2016-03-04] Demo featuring the WP visual rich text editor (TinyMCE), including the insertion of images from the media library. Post content can be edited in the Customizer and previewed in multiple contexts. For example, this allows you to preview how a Read More tag will appear when the post appears on a post list page, and you can navigate to the single post to continue previewing subsequent paragraphs. You can expand the editor into a full-screen mode to focus on writing and then quickly preview the changes on the site by toggling the editor. You can make changes to as many posts as you want, but none of the changes will go live until you hit Save & Publish: everything is previewed so there is no “save and surprise”.

[youtube https://www.youtube.com/watch?v=QJsEl0gd7dk]

[2016-03-03] Demonstration of integration with [Customize Setting Validation](https://github.com/xwp/wp-customize-setting-validation) ([#34893](https://core.trac.wordpress.org/ticket/34893)) to gracefully handle failures to save due to post locking and concurrent user editing:

[youtube https://www.youtube.com/watch?v=OUwwTt6FtlQ]

[2016-03-01] Demonstration of hooking into edit post links so that they actually work in the Customizer and expand the section to edit the given post (as opposed to the link doing nothing at all when clicked), as well as shift-clicking on the title and content (needs better discovery UI, see [#27403](https://core.trac.wordpress.org/ticket/27403)):

[youtube https://www.youtube.com/watch?v=nYfph3NbNCc]

== Screenshots ==

1. [0.7.0] Select2 dropdown in a post type's panel allows all posts of that type to be searched, including trashes. Selecting a post here causes its section to be added and expanded, with the preview then navigating to the URL for that post.
2. [0.7.0] Post status control is now accompanied by a post date control. A Move to Trash link also appears with the status control.
3. [0.7.0] Selecting a future date switches status form published to scheduled, and a countdown for when the post will be scheduled is available along with the timezone information.
4. [0.7.0] Clicking the date reset link causes the setting's date to be emptied, with the control's inputs then receiving the current date/time as placeholders which update each minute to correspond to the current date/time.

== Changelog ==

= [0.7.0] - 2016-08-06 =

Added:

 * Introduce Select2 dropdown in a post type's panel for searching for any post to load, even if it is not shown in the preview. Selecting a post adds its section to the Customizer and expands it while also navigating to the post's URL in the preview. Trashed posts are also listed, and selecting a trashed post will load its post data into the Customizer in its untrashed state (restoring its original status and slug) so that upon save it will be be untrashed. (<a href="https://github.com/xwp/wp-customize-posts/pull/196" class="issue-link js-issue-link" data-url="https://github.com/xwp/wp-customize-posts/issues/196" data-id="164758731" data-error-text="Failed to load issue title" data-permission-text="Issue title is private">#196</a>, <a href="https://github.com/xwp/wp-customize-posts/pull/199" class="issue-link js-issue-link" data-url="https://github.com/xwp/wp-customize-posts/issues/199" data-id="167144506" data-error-text="Failed to load issue title" data-permission-text="Issue title is private">#199</a>)
 * Add control for post <em>date</em>, including synchronization with publish/future status for when date is in future. Control includes timezone information and countdown for when schedule publish will happen. Also includes reset link to leave the date empty so that it will default to the current date/time when it is published. (<a href="https://github.com/xwp/wp-customize-posts/issues/56" class="issue-link js-issue-link" data-url="https://github.com/xwp/wp-customize-posts/issues/56" data-id="139950255" data-error-text="Failed to load issue title" data-permission-text="Issue title is private">#56</a>, <a href="https://github.com/xwp/wp-customize-posts/pull/202" class="issue-link js-issue-link" data-url="https://github.com/xwp/wp-customize-posts/issues/202" data-id="167405100" data-error-text="Failed to load issue title" data-permission-text="Issue title is private">#202</a>)
 * Improve UX for trashing posts, adding a Move to Trash link. (<a href="https://github.com/xwp/wp-customize-posts/issues/172" class="issue-link js-issue-link" data-url="https://github.com/xwp/wp-customize-posts/issues/172" data-id="159524166" data-error-text="Failed to load issue title" data-permission-text="Issue title is private">#172</a>, <a href="https://github.com/xwp/wp-customize-posts/pull/211" class="issue-link js-issue-link" data-url="https://github.com/xwp/wp-customize-posts/issues/211" data-id="169467306" data-error-text="Failed to load issue title" data-permission-text="Issue title is private">#211</a>)
 * Add initial support for meta queries when the Customizer state includes changes to postmeta. (<a href="https://github.com/xwp/wp-customize-posts/pull/174" class="issue-link js-issue-link" data-url="https://github.com/xwp/wp-customize-posts/issues/174" data-id="159564977" data-error-text="Failed to load issue title" data-permission-text="Issue title is private">#174</a>, <a href="https://github.com/xwp/wp-customize-posts/pull/191" class="issue-link js-issue-link" data-id="162754015" data-error-text="Failed to load issue title" data-permission-text="Issue title is private" title="Improve meta query support">#191</a>, <a href="https://github.com/xwp/wp-customize-posts/pull/197" class="issue-link js-issue-link" data-id="165623206" data-error-text="Failed to load issue title" data-permission-text="Issue title is private" title="Ensure meta queries work for newly-inserted auto draft posts">#197</a>, <a href="https://github.com/xwp/wp-customize-posts/pull/193" class="issue-link js-issue-link" data-url="https://github.com/xwp/wp-customize-posts/issues/193" data-id="163417852" data-error-text="Failed to load issue title" data-permission-text="Issue title is private">#193</a>)
 * Allow post field control labels to be defined in <code>register_post_type()</code> so that the names can be repurposed to be appropriate to the custom post type. (<a href="https://github.com/xwp/wp-customize-posts/pull/195" class="issue-link js-issue-link" data-url="https://github.com/xwp/wp-customize-posts/issues/195" data-id="163751896" data-error-text="Failed to load issue title" data-permission-text="Issue title is private">#195</a>)
 * Add low-fidelity live JS-applied previews to post title changes while waiting for high-fidelity PHP-applied selective refresh requests to response. (<a href="https://github.com/xwp/wp-customize-posts/issues/43" class="issue-link js-issue-link" data-url="https://github.com/xwp/wp-customize-posts/issues/43" data-id="139483578" data-error-text="Failed to load issue title" data-permission-text="Issue title is private">#43</a>)

Fixed:

 * Ensure title is focused and selected when creating a new post. (<a href="https://github.com/xwp/wp-customize-posts/issues/209" class="issue-link js-issue-link" data-url="https://github.com/xwp/wp-customize-posts/issues/209" data-id="168734888" data-error-text="Failed to load issue title" data-permission-text="Issue title is private">#209</a>, <a href="https://github.com/xwp/wp-customize-posts/pull/208" class="issue-link js-issue-link" data-url="https://github.com/xwp/wp-customize-posts/issues/208" data-id="168732561" data-error-text="Failed to load issue title" data-permission-text="Issue title is private">#208</a>, <a href="https://github.com/xwp/wp-customize-posts/pull/206" class="issue-link js-issue-link" data-url="https://github.com/xwp/wp-customize-posts/issues/206" data-id="168702760" data-error-text="Failed to load issue title" data-permission-text="Issue title is private">#206</a>)
 * Make sure that posts are loaded for any post sections/controls that are autofocused. (<a href="https://github.com/xwp/wp-customize-posts/issues/204" class="issue-link js-issue-link" data-url="https://github.com/xwp/wp-customize-posts/issues/204" data-id="168454674" data-error-text="Failed to load issue title" data-permission-text="Issue title is private">#204</a>, <a href="https://github.com/xwp/wp-customize-posts/pull/205" class="issue-link js-issue-link" data-url="https://github.com/xwp/wp-customize-posts/issues/205" data-id="168479600" data-error-text="Failed to load issue title" data-permission-text="Issue title is private">#205</a>)
 * Speed up performance by registering post/postmeta settings and partials only as they are needed (just in time), introducing a new <code>ensurePosts</code> API call to fetch the settings over Ajax and create the relevant section. (<a href="https://github.com/xwp/wp-customize-posts/pull/201" class="issue-link js-issue-link" data-url="https://github.com/xwp/wp-customize-posts/issues/201" data-id="167209668" data-error-text="Failed to load issue title" data-permission-text="Issue title is private">#201</a>)
 * Improve test coverage. (<a href="https://github.com/xwp/wp-customize-posts/pull/200" class="issue-link js-issue-link" data-url="https://github.com/xwp/wp-customize-posts/issues/200" data-id="167208162" data-error-text="Failed to load issue title" data-permission-text="Issue title is private">#200</a>)
 * Fix editor text not persistent issue across all posts and post types. (<a href="https://github.com/xwp/wp-customize-posts/issues/129" class="issue-link js-issue-link" data-url="https://github.com/xwp/wp-customize-posts/issues/129" data-id="152863642" data-error-text="Failed to load issue title" data-permission-text="Issue title is private">#129</a>, <a href="https://github.com/xwp/wp-customize-posts/pull/198" class="issue-link js-issue-link" data-url="https://github.com/xwp/wp-customize-posts/issues/198" data-id="166660326" data-error-text="Failed to load issue title" data-permission-text="Issue title is private">#198</a>)
 * Sort posts in a section reverse-chronologically by date (if non-hierarchical) or else by <code>menu_order</code> if hierarchical. (<a href="https://github.com/xwp/wp-customize-posts/issues/124" class="issue-link js-issue-link" data-url="https://github.com/xwp/wp-customize-posts/issues/124" data-id="151904091" data-error-text="Failed to load issue title" data-permission-text="Issue title is private">#124</a>)
 * Ensure changes to post status are reflected in return value when calling <code>get_post_status()</code>. (<a href="https://github.com/xwp/wp-customize-posts/pull/194" class="issue-link js-issue-link" data-url="https://github.com/xwp/wp-customize-posts/issues/194" data-id="163502015" data-error-text="Failed to load issue title" data-permission-text="Issue title is private">#194</a>)

See full commit log: [`0.6.1...0.7.0`](https://github.com/xwp/wp-customize-posts/compare/0.6.1...0.7.0)

Issues in milestone: [`milestone:0.7.0`](https://github.com/xwp/wp-customize-posts/issues?q=milestone%3A0.7)

Props: Weston Ruter (<a href="https://github.com/westonruter" class="user-mention">@westonruter</a>), John Regan (<a href="https://github.com/johnregan3" class="user-mention">@johnregan3</a>), Sayed Taqui (<a href="https://github.com/sayedwp" class="user-mention">@sayedwp</a>), Utkarsh Patel (<a href="https://github.com/PatelUtkarsh" class="user-mention">@PatelUtkarsh</a>), Luke Gedeon (<a href="https://github.com/lgedeon" class="user-mention">@lgedeon</a>), Ahmad Awais (<a href="https://github.com/ahmadawais" class="user-mention">@ahmadawais</a>), Derek Herman (<a href="https://github.com/valendesigns" class="user-mention">@valendesigns</a>), Piotr Delawski (<a href="https://github.com/delawski" class="user-mention">@delawski</a>)

= [0.6.1] - 2016-06-16 =

* Send values to JS via `js_value()` and use the settings `json` method if available.
* Move `comments_open` and `pings_open` filters to the `WP_Customize_Posts_Preview::add_preview_filters` method.
* Fix `purgeTrash` to ensure trashed post sections do not appear in the Customizer root panel after publishing changes.
* Ensure the modified date is not changed when transitioning to `customize-draft`.
* Make sure the `customize-draft` status is always available to Customize Snapshots & `wp-admin`
* Fix PHP notice generated when a post type is registered without `map_meta_cap`
* Delete `auto-draft` and `customize-draft` status posts when saving the trash `post_status`
* Use a post type's `edit_posts` capability for sections
* Defer embedding a sections contents until expanded
* Implement `focusControl` support for `deferred-embedded` post section controls
* Add support for focusing on controls for setting properties when those properties are invalid
* Prevent `customized-posts` messages sent via `selective-refresh` from effecting `post-navigation` state
* Improve feature detection for including customize-controls patched for trac-36521
* Included plugin-support and theme-support PHP files that were inadvertantly omitted from the 0.6.0 build.

See full commit log: [`0.6.0...0.6.1`](https://github.com/xwp/wp-customize-posts/compare/0.6.0...0.6.1)

Issues in milestone: [`milestone:0.6.1`](https://github.com/xwp/wp-customize-posts/issues?q=milestone%3A0.6.1)

Props: Weston Ruter (<a href="https://github.com/westonruter" class="user-mention">@westonruter</a>), Derek Herman (<a href="https://github.com/valendesigns" class="user-mention">@valendesigns</a>)

= 0.6.0 - 2016-06-02 =

Added:

 * Add the ability to create new posts and pages in the Customizer. Created posts get <code>auto-draft</code> status in the DB so they will be garbage-collected if the Customizer is never saved. A new view link appears in the post section allowing a newly-created post to be navigated to easily without having to find the created post linked to in the preview. (Issues <a href="https://github.com/xwp/wp-customize-posts/issues/48" class="issue-link js-issue-link" data-url="https://github.com/xwp/wp-customize-posts/issues/48" data-id="139489948" data-error-text="Failed to load issue title" data-permission-text="Issue title is private">#48</a>, <a href="https://github.com/xwp/wp-customize-posts/issues/50" class="issue-link js-issue-link" data-url="https://github.com/xwp/wp-customize-posts/issues/50" data-id="139490828" data-error-text="Failed to load issue title" data-permission-text="Issue title is private">#50</a>, PR <a href="https://github.com/xwp/wp-customize-posts/pull/134" class="issue-link js-issue-link" data-id="154290445" data-error-text="Failed to load issue title" data-permission-text="Issue title is private" title="Post Creation">#134</a>)
 * Add post status control and preview, with <code>trash</code> status support (Issues <a href="https://github.com/xwp/wp-customize-posts/issues/40" class="issue-link js-issue-link" data-id="138757986" data-error-text="Failed to load issue title" data-permission-text="Issue title is private" title="Add post status dropdown selection control and preview">#40</a>, <a href="https://github.com/xwp/wp-customize-posts/issues/137" class="issue-link js-issue-link" data-id="154582644" data-error-text="Failed to load issue title" data-permission-text="Issue title is private" title="Delete a post whilst in the Customizer">#137</a>, PR <a href="https://github.com/xwp/wp-customize-posts/pull/152" class="issue-link js-issue-link" data-url="https://github.com/xwp/wp-customize-posts/issues/152" data-id="157317131" data-error-text="Failed to load issue title" data-permission-text="Issue title is private">#152</a>)
 * Add support for setting validation in WordPress 4.6-alpha, showing notifications if attempting to save when a post is locked or a conflicting update was previously made. (Issue <a href="https://github.com/xwp/wp-customize-posts/issues/142" class="issue-link js-issue-link" data-url="https://github.com/xwp/wp-customize-posts/issues/142" data-id="156058078" data-error-text="Failed to load issue title" data-permission-text="Issue title is private">#142</a>, PR <a href="https://github.com/xwp/wp-customize-posts/pull/150" class="issue-link js-issue-link" data-url="https://github.com/xwp/wp-customize-posts/issues/150" data-id="156916244" data-error-text="Failed to load issue title" data-permission-text="Issue title is private">#150</a>)
 * Add the ability to vertically resize the post editor (Issue <a href="https://github.com/xwp/wp-customize-posts/issues/136" class="issue-link js-issue-link" data-url="https://github.com/xwp/wp-customize-posts/issues/136" data-id="154541791" data-error-text="Failed to load issue title" data-permission-text="Issue title is private">#136</a>, PR <a href="https://github.com/xwp/wp-customize-posts/pull/149" class="issue-link js-issue-link" data-url="https://github.com/xwp/wp-customize-posts/issues/149" data-id="156898366" data-error-text="Failed to load issue title" data-permission-text="Issue title is private">#149</a>)
 * Add post slug control, wherein changes do not cause the preview to refresh by default since there is nothing to see (Issue <a href="https://github.com/xwp/wp-customize-posts/issues/63" class="issue-link js-issue-link" data-url="https://github.com/xwp/wp-customize-posts/issues/63" data-id="140028525" data-error-text="Failed to load issue title" data-permission-text="Issue title is private">#63</a>, PR <a href="https://github.com/xwp/wp-customize-posts/pull/148" class="issue-link js-issue-link" data-url="https://github.com/xwp/wp-customize-posts/issues/148" data-id="156877309" data-error-text="Failed to load issue title" data-permission-text="Issue title is private">#148</a>)
 * Posts data as saved will now be synced back into the Customizer interface, ensuring that if a post slug gets the infamous <code>-2</code> added, you’ll see that in the Control. Likewise, if a <code>wp_insert_post_data</code> filter or <code>content_save_pre</code> changes your data in some way, these will be shown in the post’s Customizer controls upon saving.
 * Add extendable theme &amp; plugin compatibility classes that can configure partial rendering. All Core themes &amp; Jetpack are currently supported. (Issues <a href="https://github.com/xwp/wp-customize-posts/issues/82" class="issue-link js-issue-link" data-url="https://github.com/xwp/wp-customize-posts/issues/82" data-id="145302561" data-error-text="Failed to load issue title" data-permission-text="Issue title is private">#82</a>, <a href="https://github.com/xwp/wp-customize-posts/issues/103" class="issue-link js-issue-link" data-url="https://github.com/xwp/wp-customize-posts/issues/103" data-id="150771094" data-error-text="Failed to load issue title" data-permission-text="Issue title is private">#103</a>, PR <a href="https://github.com/xwp/wp-customize-posts/pull/123" class="issue-link js-issue-link" data-url="https://github.com/xwp/wp-customize-posts/issues/123" data-id="151805533" data-error-text="Failed to load issue title" data-permission-text="Issue title is private">#123</a>)
 * Use <code>plugins_url()</code> for each asset URL so that the plugin can be installed as a submodule without <code>SCRIPT_DEBUG</code> (Issue <a href="https://github.com/xwp/wp-customize-posts/pull/133" class="issue-link js-issue-link" data-url="https://github.com/xwp/wp-customize-posts/issues/133" data-id="154007394" data-error-text="Failed to load issue title" data-permission-text="Issue title is private">#133</a>)

Fixed:

 * Add all postmeta settings for registered types not just the ones actually referenced (Issues <a href="https://github.com/xwp/wp-customize-posts/pull/141" class="issue-link js-issue-link" data-url="https://github.com/xwp/wp-customize-posts/issues/141" data-id="155671511" data-error-text="Failed to load issue title" data-permission-text="Issue title is private">#141</a>, <a href="https://github.com/xwp/wp-customize-posts/issues/145" class="issue-link js-issue-link" data-url="https://github.com/xwp/wp-customize-posts/issues/145" data-id="156801928" data-error-text="Failed to load issue title" data-permission-text="Issue title is private">#145</a>)
 * Export all registered post types to client, but only register panels if <code>show_in_customizer</code> (PR <a href="https://github.com/xwp/wp-customize-posts/pull/130" class="issue-link js-issue-link" data-url="https://github.com/xwp/wp-customize-posts/issues/130" data-id="152866156" data-error-text="Failed to load issue title" data-permission-text="Issue title is private">#130</a>)
 * Ensure that control pane expand button is visible when editor is open and the Customizer pane is collapsed (Issue <a href="https://github.com/xwp/wp-customize-posts/issues/44" class="issue-link js-issue-link" data-url="https://github.com/xwp/wp-customize-posts/issues/44" data-id="139484076" data-error-text="Failed to load issue title" data-permission-text="Issue title is private">#44</a>, PR <a href="https://github.com/xwp/wp-customize-posts/pull/126" class="issue-link js-issue-link" data-url="https://github.com/xwp/wp-customize-posts/issues/126" data-id="152710123" data-error-text="Failed to load issue title" data-permission-text="Issue title is private">#126</a>)
 * Improve compatibility with the Customize Snapshots plugin.
 * Improve compatibility with the WP REST API plugin.
 * Supply a default <code>(no title)</code> placeholder to the post title control for new posts.
 * Filter post and page links in the Customizer to return the preview URL.

See full commit log: [`0.5.0...0.6.0`](https://github.com/xwp/wp-customize-posts/compare/0.5.0...0.6.0)

Issues in milestone: [`milestone:0.6`](https://github.com/xwp/wp-customize-posts/issues?q=milestone%3A0.6)

Props: Weston Ruter (<a href="https://github.com/westonruter" class="user-mention">@westonruter</a>), Derek Herman (<a href="https://github.com/valendesigns" class="user-mention">@valendesigns</a>), Philip Ingram (<a href="https://github.com/pingram3541" class="user-mention">@pingram3541</a>), Daniel Bachhuber (<a href="https://github.com/danielbachhuber" class="user-mention">@danielbachhuber</a>), Stuart Shields (<a href="https://github.com/stuartshields" class="user-mention">@stuartshields</a>)

= 0.5.0 - 2016-04-27 =

Added:

* Support for postmeta, including a framework for registering postmeta types. (Issues #1, PR #89)
* Page template control and preview, with sync from Customizer post preview back to post edit screen. (Issue #85, PR #89)
* Featured image control, with sync from Customizer post preview back to post edit screen. Changes to the featured image can now be previewed, where normally this is not possible in WordPress. Improved featured image selection on edit post screen to not update featured image in place, instead waiting until the post is Saved until updating the featured image postmeta. The featured image can be set from the post edit screen and then previewed in the Customizer via the post Preview Changes button: the featured image can be further changed in the Customizer post preview, with changes synced back to the post edit screen when the Customizer post preview is exited. (Issue #57, PR #102)
* Author control and preview, with sync from Customizer post preview back to post edit screen (Issue #62, PRs #89 #92)
* Excerpt control and preview, with sync from Customizer post preview back to post edit screen (Issue #60, PR #91)
* Comment status control and preview, with sync from Customizer post preview back to post edit screen (Issues #61, PR #100)
* Ping status control and preview, with sync from Customizer post preview back to post edit screen (Issue #64, PR #100)
* Improve PHPUnit test coverage to 98%.
* Note: Selective refresh support was specifically tested with Twenty Fifteen and Twenty Sixteen. See #103 for a way for themes to configure how they represent the various post fields in template parts.

Fixed:

* Improve editor styles in mobile and in fullscreen mode. (Issue #45, PR #107)
* Modals, toolbars, and tooltips and are no longer hidden (Issue #80, PRs #81, #101).
* Improve compatibility with Customize Widgets Plus (PR #83). See also https://github.com/xwp/wp-customize-widgets-plus/pull/46 for a fix in the Customizer post preview.
* Export post/postmeta settings during selective refresh requests so that new posts added will appear in the panel, such as when adding the number of posts to show in the Recent Posts widget. (Issue #97, PR #99)
* Improve compatibility with Customize Snapshots (PR #95)

See [v0.5 release post](https://make.xwp.co/2016/04/29/customize-posts-v0-5-released/) on Make XWP.

See full commit log: [`0.4.2...0.5.0`](https://github.com/xwp/wp-customize-posts/compare/0.4.2...0.5.0)

Issues in milestone: [`milestone:0.5`](https://github.com/xwp/wp-customize-posts/issues?q=milestone%3A0.5)

Props: Weston Ruter (@westonruter), Derek Herman (@valendesigns), Luke Carbis (@lukecarbis), Mike Crantea (@mehigh), Stuart Shields (@stuartshields)

= 0.4.2 - 2016-03-30 =
Restore stylesheet erroneously deleted during `grunt deploy`.

= 0.4.1 [YANKED] =
* Restore editability of pages in the Customizer (remove default condition that a post type have `publicly_queryable` as `true`).
* Log errors in `customize-posts` message receiver instead of throwing them.

= 0.4.0 - 2016-03-29 =
* Open Customizer to preview and make additional changes when clicking Preview from post edit admin screen (see [video](https://www.youtube.com/watch?v=Q62nav1k4gY)).
* Introduce `show_in_customizer` arg for `register_post_type()`, and let override condition on `show_ui` ~~and `publicly_queryable`~~ being both true.
* Fix modals and inline toolbars in TinyMCE editor displayed in Customizer.
* Fix initialization when TinyMCE does not default to Visual.
* Complete support for Jetpack Infinite Scroll, ensuring posts are listed in Customizer in order of appearance.
* Remove dependency on widgets component being loaded.
* Allow auto-draft posts to be previewed.
* Add Grunt, contributing.

= 0.3.0 - 2016-03-08 =
* Complete rewrite of plugin.
* Added: Selective refresh is now used to preview changes to the title and content.
* Added: A TinyMCE editor is now used to edit content, including initial support for Shortcake.
* Added: Each post type has a separate panel. Each post is represented by a section within those panels.
* Added: Edit post links in Customizer preview now open post section.
* Added: Integration with [Customize Setting Validation](https://github.com/xwp/wp-customize-setting-validation) to show show error message when post locking or version conflict happens.
* Removed: Postmeta fields (custom fields, page template, featured image) were removed for rewrite but will be re-introduced.

= 0.2.4 - 2016-01-06 =
Remove shim that implemented the `customize_save_response` filter which was introduced in 4.2. The shim used a slightly different filter name and broke insertion of nav menu items in the Customizer.

= 0.2.3 - 2015-01-09 =
Change method for registering scripts/styles to fix conflict w/ Jetpack. [PR #26](https://github.com/xwp/wp-customize-posts/pull/26)

= 0.2.2 - 2014-12-12 =
Add compatibility with WordPress 4.1 now that the Customizer has a proper JS API.

= 0.2.1 - 2014-09-22 =
Supply missing `selected` attribute on `post_status` dropdown.

= 0.2.0 - 2014-09-17 =
Initial release on WordPress.org. Key new features:

* Postmeta can now be added, modified, and deleted—all of actions which are fully previewable.
* Grant `customize` capability to authors and editors who normally can't access the Customizer, so they can edit posts there.
* Move the “Customize” admin bar link to the top level, and add one for editors and authors.
* Allow the Page Template and Featured Image to be modified and previewed.
