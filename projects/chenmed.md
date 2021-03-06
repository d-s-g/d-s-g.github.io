---
layout: landing
title: ChenMed
description: 
image: assets/images/chenmed.png
permalink: projects/chenmed
---

<!-- Main -->
<div id="main">

<!-- One -->
<section id="one">
	<div class="inner">
		<header class="major">
			<h2>Projects</h2>
		</header>
		<p>ChenMed is a senior healthcare provider in the US healthcare market. They have 3 main brands that serve several markets in the United States. These markets include JenCare Senior medical centers and (Virginia, Georgia, Illinois, Kentucky and Louisiana) Chen Senior medical centers (Miami, Florida) Dedicated Medical centers, (Tampa Bay, Florida & Lakeland, Florida). ChenMed also has 3 internal business sites that were worked on.
        <br><br>Development Environment ChenMed is a large Drupal 8 project, with 2 different multi-sites at its core. 1 external and 1 internal as well as supporting APIs. The frontend of the site is sass - es6 - twig.</p>
	</div>
</section>

<!-- Two -->
<section id="two" class="spotlights">
	<section>
		<div class="content">
			<div class="inner">
				<header class="major">
					<h3>ChenMed Leadership page</h3>
				</header>
<p>
I built and architected the implementation of a leadership team by market.
This includes the creation of a leadership content type, rendering content by leadership taxonomy name as a view, and then linking to the leadership page.
    <br>
    The rendered content was then templated with twig and the content styled with sass, BEM and flexbox. This project was then featurized as a drupal feature and pushed to all other ChenMed brands.
</p>
				<ul class="actions">
					<li><a href="https://www.jencaremed.com/about-us/market-leadership/richmond-virginia-leadership" class="button" target="_blank" rel="noreferrer">Visit project</a></li>
				</ul>
			</div>
		</div>
	</section>
	<section>
		<div class="content">
			<div class="inner">
				<header class="major">
					<h3>ChenMed Newsroom</h3>
				</header>
				<p>I built and architected the implementation of a newsroom utilizing
the default Article content type. Rendering content with views and handling sub taxonomies, the content was then rendered with twig and content styled
with sass, BEM and flexbox.
				</p>
				<ul class="actions">
					<li><a href="https://www.chenmed.com/news" class="button" target="_blank" rel="noreferrer">View project</a></li>
				</ul>
			</div>
		</div>
	</section>
	<section>
		<div class="content">
			<div class="inner">
				<header class="major">
					<h3>Paragraph locations module</h3>
				</header>
				<p>As a growing company, ChenMed needed a way to show locations on landing pages. These locations needed to be pulled in dynamically based on new locations that are created by the client.
                <br><br>
                For this reason the internal locations api module is consumed for this map module. The client also requested two different states to exist. The first was a locations state where each location is displayed in list view and the link directs the user to the 'brands relevant location page'. 
The second state is the one displayed at "link to winning physicians" where the map shows as a view and the links direct the user to jobs. 
    <br><br>
Moreover, to make things a little more challenging, the map needed to pull in correct location data from the correct brand(That is - locations on JenCare display JenCare locations, ChenMed displays all etc). To do this, I needed to access a locations api built by a senior developer and pull in the correct location data by brand. Then based on the state the user passed to the drupal backed. This would trigger a different display state, styling and use different data from the internal api.
    <br><br>
   The view below is the the jobs state of the map.
    </p>
				<ul class="actions">
					<li><a href="https://www.chenmed.com/winning-physicians" class="button" target="_blank" rel="noreferrer">View project</a></li>
				</ul>
			</div>
		</div>
	</section>
	<section>
		<div class="content">
			<div class="inner">
				<header class="major">
					<h3>Dynamic content type creation</h3>
				</header>
				<p>This task was architected by a senior developer but implemented by myself. This internal api uses the drupal module json api, which creates a simple paginated json api from a drupal content type.
Using this api endpoint, I implemented a hook to create new care providers in an internal Drupal 8 site. This program checked taxonomy types like location and then created a list of care providers that  were listed out in a prebuilt frontend list.
</p>
			</div>
		</div>
	</section>

</section>

</div>
