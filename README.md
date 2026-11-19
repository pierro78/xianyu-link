# xianyu-link
script to get xianyu items links from the xianyu android app through adb

HELP AND DISCUSSION : https://www.reddit.com/r/xianyulink/comments/1xx927y/android_app_get_xianyugoofish_item_links_without/

## Bookmarklet for seller pages

Tested Working on Linux Google Chrome : On goofish.com seller pages (`/personal?userId=…`) opened without being logged in, a big login box hides the seller's info and blocks scrolling. Create a bookmark with this line as its URL, then click it on the seller page:

```
javascript:(function(){var K='.ant-modal-root,.ant-modal-mask,.ant-modal-wrap',L='style[id^="rc-util-locker"]',d=document,h=d.documentElement;function f(){d.querySelectorAll(K).forEach(function(e){var p=e.parentElement;e.remove();if(p&&p!==d.body&&!p.children.length)p.remove()});d.querySelectorAll(L).forEach(function(e){e.remove()});[h,d.body].forEach(function(e){e.classList.remove('ant-scrolling-effect');['overflow','overflow-y','height','max-height','position','width','top','pointer-events','touch-action'].forEach(function(p){e.style.removeProperty(p)})})}f();var s=d.getElementById('__unlock');if(!s){s=d.createElement('style');s.id='__unlock';d.head.appendChild(s)}s.textContent='html,body{overflow:auto!important;overflow-y:auto!important;max-height:none!important;position:static!important;pointer-events:auto!important;touch-action:auto!important}body{height:auto!important;width:auto!important}'+K+'{display:none!important}';d.querySelectorAll('body *').forEach(function(e){var c=getComputedStyle(e),r;if((c.position=='fixed'||c.position=='absolute')&&+c.zIndex>0){r=e.getBoundingClientRect();if(r.width>=innerWidth*.9&&r.height>=innerHeight*.9)e.style.setProperty('pointer-events','none','important')}});if(!window.__unl){window.__unl=1;['wheel','mousewheel','touchmove'].forEach(function(t){window.addEventListener(t,function(e){e.stopImmediatePropagation()},{capture:true,passive:true})});new MutationObserver(function(){if(d.querySelector(K+','+L)||h.classList.contains('ant-scrolling-effect')||d.body.classList.contains('ant-scrolling-effect'))f()}).observe(h,{childList:true,subtree:true,attributes:true,attributeFilter:['class']})}})();
```

It removes the login box and its overlay, re-enables scrolling, and removes the box again if the site brings it back.

## Versions

V3.2 : seller info (rating, credit, on sale, IP province, last online, shop badge) + seller screenshot ; "?" when shop/individual is a guess ; --last: + / - to zoom the screenshot (0 = reset) ; fixes: item shown after leaving it, Xianyu restart, revisited sellers

V3.1 : pbcopy (macOS)

V3.0 : initial github release
