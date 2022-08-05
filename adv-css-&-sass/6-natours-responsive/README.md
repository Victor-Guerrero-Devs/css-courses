# 6. Natours Responsive Design

The final module to the Natours project. We implement responsive design to it. 

## Intro 

So far, we have been building this project desktop-first. This is not how websites are generally developed these days. Instead, most start designing for mobile first and then using media-queries to accomodate tablets, laptops, and desktops. 

### Benefits of mobile-first design

- most internet users are mobile users 
- reduces bloat for the mobile experience 
- easier to design for mobile b/c there is less room to work with 

### Cons of mobile-first design

- does your userbase primarily use mobiles? 
- desktop version may look too bare 
- more constrained design choice 

### Breakpoints

Bad Breakpoints
- using the widths of the latest iPhone, iPad, mac, etc 
- everytime a new version comes out, you'll need to change your break points 

Good Breakpoints 
- using the average widths of the most popular phones, tablets, laptops 

Best Breakpoints 
- making breakpoints designed around your layout 
- whenever your layout break, you make a new breakpoint to fix it 

https://www.browserstack.com/guide/ideal-screen-sizes-for-responsive-design

According to this, the 3 most popular resolutions in 2021 were: 

1. 1920x1080 
2. 1366x768
3. 360x640

## SASS + Breakpoints 

The best way to add media queries with SASS is to to go into the individual components in `sass/components/` and add media queries directly inside the selectors 
- this is the same idea as in Mosh's course where he added a media query at the end of every component/section specific to that thing 


