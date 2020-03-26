# Auro Compliance: A vs. AA vs. AAA

To better understand Auro compliance, it may be easier to visualize an inverted triangle or a funnel. The top of the triangle, with the widest reach, is also the most generic. This is where the Design Tokens are. Funneling down, the next layer is WCSS. More specific in use and has a dependency on the Design Tokens. Next are the Icons. With an even more specific use case and a dependency on both WCSS and Design Tokens. In the final part of the funnel are the Web Components. Here things are explicit. Web Components have a direct dependency on Design Tokens and may or may not have a dependency on WCSS and Icons. 

Following this layering of resources, a compliance model can be created. 

```
    __________
    \________/     Tokens
     \______/      WCSS
      \____/       Icons
       \__/        Web Components
   
```

### Level A

To meet level A compliance, developers simply need to be using Design Tokens as a resource. 

At this level, developers are using a shared resource for base variables but constructing all their UIs locally without any influence from the Design System. 

This level is the easiest to achieve and it is suggested that every team meet this level. 

### Level AA

To meet level AA compliance, it’s important that developers use as much of the WCSS library as makes sense for their project. WCSS has a direct dependency on Design Tokens, so any tools used from WCSS will be compliant. 

In addition to using WCSS and Design Tokens, in order to be 100% compliant with AA standards, the project must also use 100% of the Design Tokens that make sense in their project. Duplication of value in a local variable or hard-coded into the project will deem the project non-compliant.

Lastly, the use of icons is required to use the approved Auro SVGs. Any duplication of SVG code or use of a PNG, JPEG or GIF to represent the Auro icon would deem the project non-compliant. 

### Level AAA

The Success Criterion for AAA has a few challenges for product teams. Not only are teams required to meet the minimum requirements for Level A and AA but the project must use Auro Web Components when applicable. 

Any reproduction of a standardized UI web component locally in a project would deem the project non-compliant. 


### Breaking the triangle 

Given the independent nature of the Auro Design System, there are opportunities to break the triangle and use only some of the resources in a given project.

While these options are possible, it is suggested to adhere to the compliance model as much as possible as this will cause the least amount of issues. 
