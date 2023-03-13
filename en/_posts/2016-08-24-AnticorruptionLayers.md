---
layout: post_img
author: fausto
title: Anticorruption Layers
image: /assets/images/capas_anticorrupcion.jpeg
---
That panic moment when the decision of changing the application X which our systems depend on is made.
<br/><br/>

When we build systems, most of the times those systems depend on or need external or third party applications. The moment when one of these external applications need to be changed or an updated is needed is when the problems don’t stop.<br/><br/>

The biggest problem most of the time is not the new application or the new version doesn’t have the same features than the older one (in fact they tend to have cooler features or more of them), the problem is that our system is invaded with dependencies of the external application; the problem is that our domain is corrupted by an external domain.<br/><br/>

![Figure 1](/assets/images/figure2_capas.jpg)<br/><br/>

For instance, we have a system (green boxes) that manages, besides other features, files and documents, so it has been decided to use a file repository like Alfresco or FileNet (yellow box). Alfresco (or any other tool) provides libraries or API’s that are used by our system to make the integration. In this point our system/domain has an external dependency along multiple components, and that’s why we say our domain is corrupted because the external domain is allocated everywhere. The moment we will decide to switch the the yellow box by a red one we will need to seek every single dependency in our domain and make the change for the new one.<br/><br/>

We can avoid this problem introducing an Anticorruption Layer (a term coined in the book DDD) that allows us to isolate the external or third-party dependencies, whether these are tools, systems, libraries, different domains, etc..<br/><br/>


![Figure 1](/assets/images/figure3_capas.jpg)<br/><br/>

The idea is to build a layer between our domain and the external dependency. This layer is the responsible to do the transformations in both ways; it means, transform the components of our domain into components that the external tool can understands, and vice versa. This way we can isolate the dependency in one single place, so our domain (green boxes) is focus on solving the problem, and any change in the external dependency won’t affect substantially our system behavior.