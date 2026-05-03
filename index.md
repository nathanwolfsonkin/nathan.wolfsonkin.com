---
---

{% capture left %}
{:.center}
<div style="
  font-size: 2.25rem;
  font-weight: 700;
  letter-spacing: 0.08em;
  color: rgba(0, 0, 0, 0.92);
  font-family: var(--title);
">
  NATHAN WOLF-SONKIN
</div>

{:.center}
<div style="
  margin-top: 0.5rem;
  font-size: 1.5rem;
  font-weight: 400;
  color: rgba(30, 30, 30, 0.65);
">
  Doctoral Student at the Temple University Robotics and AI Lab
</div>


<div style="margin-top: 1.25rem;">
  {% include button.html
    text="Resume"
    link="resume.pdf"
    new_tab=true
  %}
</div>

{% endcapture %}

{% capture right %}
{% include figure.html
   image="/images/nathan_wolf-sonkin.jpg"
   width="80%"
%}
{% endcapture %}

{% include cols.html
   col1=left
   col2=right
%}