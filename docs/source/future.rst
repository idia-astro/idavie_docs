.. _future:

Future Plans
============

While iDaVIE has many useful features already, there are still many features that would be of significant use to scientists. We have a roadmap that we will continue to direct iDaVIE's development along, and provide an overview of our future plans.

In the **short** term, we list features that we are actively working on and will be included in the next major release. This is not an exhaustive list and will be added to as development progresses. **Medium**-term goals are major feature additions that will require several weeks to months of dedicated development, with an initial idea or prototype already available. **Long**-term plans are major features that are dreams still, with no concrete plans on how to implement them yet.

Short-term
----------
* Improve the performance of the scripted video rendering.
* Separate the visualisation from the analysis tools. At the moment, much of the radio astronomy analysis tools and the visualisation are hardcoded together, such as the menus. The actual analysis code is contained within a `.dll` plugin. Unity allows for dynamically created menus (see the generic popups in the subcube `pull request <https://github.com/idia-astro/iDaVIE/pull/320>`_), which opens the possibility of moving all analysis tools into a separate plugin, while the visualisation code remains as is. Creators of the analysis tools can then potentially specify their menus through a script or API file, while iDaVIE (the visualisation tool) creates the menus dynamically from prefabs. More work will be required to look at how Unity deals with dynamic code, as well as a major refactor once the framework is made possible. This will be of significacnt use in the multidisciplinary domain, allowing the end user to download iDaVIE the visualisation tool and the analysis plugin relevant to their field. See the related `issue <https://github.com/idia-astro/iDaVIE/issues/405>`_ and `discussion <https://github.com/idia-astro/iDaVIE/discussions/408>`_ for more information.
* Release a version of iDaVIE that allows for particle datasets to be visualised. In particular, sparse multiparameter datasets, such as simulations, benefit greatly from visualisation in VR. A prototype has been created and sample images can be found on our `documentation pages <https://idavie.readthedocs.io/en/latest/multidisciplinary.html>`_. A publicly available prototype will be available in due course.

Medium-term
-----------
* Allow users to switch between rendering for emission or absorption. At the moment, the rendering shader (a ray-marching algorithm) samples values along the ray and returns either the maximum or the average value. To account for absorption in the foreground, a new shader will have to be developed, possibly based on `radiative transfer <https://en.wikipedia.org/wiki/Radiative_transfer>`_ equations. See the relevant `issue <https://github.com/idia-astro/iDaVIE/issues/256>`_ and `discussion <https://github.com/idia-astro/iDaVIE/discussions/403>`_ for more information.
* Allow for a movable projection plane that highlights a 2D cross-section in a separate window, akin to the existing moment maps feature. This can be a single channel, or a position-velocity graph, or potentially overlaying one dataset on another. See `the <https://github.com/idia-astro/iDaVIE/issues/74>`_ `relevant <https://github.com/idia-astro/iDaVIE/issues/197>`_ `issues <https://github.com/idia-astro/iDaVIE/issues/404>`_ and `discussion <https://github.com/idia-astro/iDaVIE/discussions/407>`_ for more information.

Long-term
---------
* Integrating a Python console into the application.
* Adding additional visualisation modes, such as isocontours, for example.
* Creating a multiplayer or spectator mode. For spectator mode, one user will be the controller, and any subsequent user will only see the cube as the controller sees it, though they can move around separately.
* Integrating a VO system, allowing for a dynamic retrieval of images from data catalogues in other wavelengths for the patch of sky corresponding to the currently loaded cube. This will require sending cutout requests to the servers hosting said catalogues, which might require authentication.
* Visualising multiple cubes simultaneously, or visualising a time-series. This will require significant work to be performant, given the size of existing cubes and the bottleneck provided by limited memory.
* Allow for state or workspace saving. This is a fairly standard feature in many visualisation software (such as CARTA), and would be good to have for iDaVIE. This will require a careful design to take care of what is saved, and how to call the relevant functions when loading the saved state.