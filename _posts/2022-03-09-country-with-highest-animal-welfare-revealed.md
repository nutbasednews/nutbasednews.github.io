---
layout: post
title:  "Country with highest animal welfare standards revealed"
author: nutbasednews
categories: [ Ethical meat, Local farms ]
image: assets/images/posts/2022-03-09-country-with-highest-animal-welfare-revealed/0.png
tags: [ featured ]
---

Ask anyone which country has the highest animal welfare standards in the world, and their answer will likely be, *"My country has the highest animal welfare standards! I only buy my meat from where I live"*.

The **most extensive research** has been published by one of the **oldest established farmer associations** in the world. We can now reveal with certainty which country provides the best care for their farmed animals and how it compares to <span class="country country-emphasise no-change">your country</span>.

## An unsurprising winner...

<div class="relative" markdown="1">
**<span class="country country-emphasise" style="text-transform: capitalize;">Your country</span>** was found to have the highest animal welfare standards globally, beating the likes <span class="country-random country-emphasise">your neighbouring country</span>, <span class="country-random country-emphasise">the one you hate</span> or even <span class="country-random country-emphasise">the one you love that isn't your country</span>.

The winner was revealed in the latest report published by the **Global Meat, Dairy and Eggs Association of <span class="country country-emphasise">Your Country</span>**.

One example of <span class="country">your country</span>'s animal welfare standard is the separation of newborns calves from their mothers. The country supports this practice to stop cows from crushing their baby. If the calf is male and therefore **deemed a waste product of the dairy industry**, <span class="country country-emphasise">your country</span> allows farmers to send them for **slaughter at a very young age** to make **veal** out of them.

![Waste product of the dairy industry]({{ site.base_url }}/assets/images/posts/2022-03-09-country-with-highest-animal-welfare-revealed/1.png)

Other examples of welfare standards can be found in the report, confirming that <span class="country country-emphasise">your country</span> is a global leader in animal welfare.

The findings aren't that surprising, as farmers of <span class="country country-emphasise">your country</span> has always been praised for their high level of care toward their animals. If other countries had to follow the example of one country when it comes to animal welfare, <span class="country country-emphasise">your country</span> would be that country.

The findings aren't that suprising, as <span class="country country-emphasise">Your country</span> has always been praised for the high level of care its farmers provide to their animals. **If other countries had to follow the example of one country when it comes to animal welfare, <span class="country country-emphasise">your country</span> would be that country.**

<div class="modal-container hidden">
   <div class="modal-backdrop absolute z-0 top-0 bottom-0 left-0 right-0"></div>
   <div class="country-modal shadow-2xl rounded-lg relative z-10" style="font-family: 'Segoe UI', 'Helvetica Neue', 'Arial'">
      <div class="row align-items-start spanborder mb-0">
         <div class="col-2">
            <div class="pl-4 pt-8">
               🥩
            </div>
         </div>
         <div class="col-10">
            <h6 class="mb-2 mr-4">Which country does your meat comes from?</h6>
            <small class="text-xs leading-snug block mb-4 mr-4 text-zinc-400">To find out how ethical your meat is</small>
         </div>
      </div>
      <div class="overflow-y-auto overflow-x-hidden h-96 ">
         <ul class="list-unstyled pt-2"></ul>
      </div>
      <div class="p-2">
         <a class="btn btn-success w-full country-guess-btn" href="">Skip this step</a>
      </div>
   </div>
</div>

<div class="toast sticky bottom-0 left-0 right-0 flex justify-center align-center py-3 transition-all" style="z-index: 9999; opacity: 0;">
   <div class="bg-white drop-shadow-xl rounded-md px-3 pt-2 pb-3 leading-tight w-100">
      <small class="text-sm">
         <strong class="text-slate-600">We are having technical difficulties:</strong>
         <br>
         <span class="text-slate-500"><span class="country country-emphasise capitalize no-change">Your country</span> definitely has the best standards 👍</span>
      </small>
   </div>
</div>
</div>

<script src="{{ site.base_url }}/assets/js/countries.js"></script>
<script>
   let param = new URLSearchParams(window.location.search).get('country');


   let initCountryModal = () => {
      let modal = document.querySelector('.country-modal');
      countries.forEach((country) => {
         var s = `<li><a class="row align-items-center pl-4 text-base" style="font-family: 'Segoe UI', 'Helvetica Neue', 'Arial'" href="${window.location.pathname}?country=${country.iso2}"><img class="col-2 m-0" src="${country.flag}"><span>${country.name}</span></a></li>`;
         var temp = document.createElement('div');
         temp.innerHTML = s;
         var listItem = temp.firstChild;
         modal.querySelector('ul').append(listItem);
      });
   }

   let modalContainer = document.querySelector('.modal-container');

   let openModal = () => {
      document.querySelector('body').classList.add('overflow-y-hidden')
      modalContainer.classList.add('flex');
      modalContainer.classList.remove('hidden');
   }

   let closeModal = () => {
      document.querySelector('body').classList.remove('overflow-y-hidden')
      modalContainer.classList.remove('flex')
      modalContainer.classList.add('hidden');
   }

   document.querySelectorAll('.country').forEach((el) => {
      el.addEventListener('click', (el) => {
         openModal();
      })
   });

   document.querySelector('.modal-backdrop').addEventListener('click', closeModal);
   initCountryModal();

   let setMainCountry = (country, with_exception) => {
      if (!country) return;

      document.querySelectorAll(`.country${with_exception ? ':not(.no-change)' : ''}`).forEach((el) => {
         let name = country.short || country.name;
         let emphasise = country.emphasise && el.classList.contains('country-emphasise');
         el.textContent = (emphasise ? 'the ' : '') + name;
      });
   }

   let setRandomCountries = (country) => {
      document.querySelectorAll('.country-random').forEach((el) => {
         let rand = getRandomCountry(country);
         let name = rand.short || rand.name;
         let emphasise = rand.emphasise && el.classList.contains('country-emphasise');
         el.textContent = (emphasise ? 'the ' : '') + name;
      });
   }

   let randomBetween = (min, max) => parseInt(Math.random() * (max - min) + min);

   let getRandomCountry = (current) => {
      let min = 0;
      let max = countries.length - 1;
      let index = randomBetween(min, max);

      let selectedCountry = countries[index]

      return (!current || selectedCountry.iso2 !== current.iso2) ? selectedCountry : getRandomCountry(current);
   };

   let glitch = (currentCountry, iterations) => {
      if (iterations === 5) {
         let toast = document.querySelector('.toast');
         toast.classList.add('flex');
         toast.classList.remove('hidden');
         toast.style.opacity = 1;
      }

      setTimeout(() => {
         let newCurrentCountry = getRandomCountry(currentCountry);
         setMainCountry(newCurrentCountry, true);
         let opacity = randomBetween(10, 100) / 100.0;
         document.querySelectorAll('.country:not(.no-change)').forEach((el) => {
            el.classList.add('wrong-country');
            el.style.transform = `rotate(${randomBetween(-6, 6)}deg) translate3d(${randomBetween(-6, 6)}px,${randomBetween(-6, 6)}px,0)`;
         });
         setTimeout(() => {
            setMainCountry(currentCountry);
            document.querySelectorAll('.country:not(.no-change)').forEach((el) => {
               el.classList.remove('wrong-country');
               el.style.transform = `rotate(${randomBetween(-6, 6)}deg) translate3d(${randomBetween(-6, 6)}px,${randomBetween(-6, 6)}px,0)`;
            });
            glitch(currentCountry, iterations + 1);
         }, randomBetween(50, 1000))
      }, randomBetween(250, 4000))
   }

   let initCountry = (iso2) => {
      let countryCode = iso2.toUpperCase();
      let country = countries.find((country) => country.iso2 === countryCode.toUpperCase());

      if (!country) {
         setMainCountry(country);
      }
      setRandomCountries(country);
      glitch(country, 0);
   }

   document.querySelector('.country-guess-btn').addEventListener('click', (e) => {
      e.preventDefault();
      let language = navigator.language;

      if (language) {
         let iso2 = language.split('-')[1];

         if (iso2) {
            window.location = `${window.location.origin}${window.location.pathname}?country=${iso2}`;
         } else {
            closeModal();
         }
      }
   });


   if (param) {
      initCountry(param);
   } else {
      openModal();
   }
</script>

<style type="text/tailwindcss">
   .country:not(.no-change) {
      @apply cursor-pointer;
      @apply transition-all;
      @apply animate-pulse;
      @apply bg-slate-200;
      @apply inline-block;
      @apply rounded-sm;
      @apply px-1;
   }
   .wrong-country {
      @apply translate-x-0.5;
      @apply -rotate-6;
   }
</style>
