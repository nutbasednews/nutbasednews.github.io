---
layout: post
title:  "Country with highest animal welfare revealed"
author: nutbasednews
categories: [ Ethical meat ]
image: assets/images/posts/2022-03-07-country-with-highest-animal-welware-revealed/0.png
tags: [ featured ]
---

<span class="country country-emphasise" style="text-transform: capitalize;"></span> was found to have the highest animal welfare in the world, beating the like of <span class="country-random country-emphasise"></span>, <span class="country-random country-emphasise"></span> or even <span class="country-random country-emphasise"></span>.

In the latest report published by <span class="country country-emphasise"></span> Global Farmer Association, <span class="country"></span>'s farmed animals may very likely have the best life out of all farmed animals in the world. 

<span class="country"></span>'s chickens are the luckiest chicken in the world. They are treated like they are family, and sent for slaughter in the best conditions as possible

When it comes to pigs, it’s the same story. <span class="country"></span> pigs are loved and treated with proper care. The animals have enough space to stretch they body and be as close to their litters.

Regarding dairy cows, <span class="country country-emphasise"></span> is following a similar pattern. Calves are taken away from their mothers at birth to make sure the babies are never hurt by their mothers.

If other countries had to follow the example of one country when it comes to animal welfare, <span class="country country-emphasise"></span> would be that country.

<script src="{{ site.base_url }}/assets/js/countries.js"></script>
<script>
   let getRandomCountry = () => {
      let min = 0;
      let max = countries.length - 1;
      let index = parseInt(Math.random() * (max - min) + min);

      return countries[index];
   };

   let countryCode = new URLSearchParams(window.location.search).get('country');

   let country = countries.find((country) => country.iso2 === countryCode.toUpperCase());
   let name = country.short || country.name;

   document.querySelectorAll('.country').forEach((el) => {
      let emphasise = country.emphasise && el.classList.contains('country-emphasise');
      el.textContent = (emphasise ? 'the ' : '') + name;
   });

   document.querySelectorAll('.country-random').forEach((el) => {
      let country = getRandomCountry();
      let name = country.short || country.name;
      let emphasise = country.emphasise && el.classList.contains('country-emphasise');
      el.textContent = (emphasise ? 'the ' : '') + name;
   });
</script>

