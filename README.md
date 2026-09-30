# Element remover (temporary) - Chrome extension.
Remove any elements from page (work with iframe)  
(It can be useful, for example, when removing elements BEFORE printing - in order to save ink in the printer or help remove elements from the page before taking a screenshot)

Exit - press "q" key

Undo - press "ctrl+z" keys

Select mouse on element (red box) - click to DELETE or use "Del" key (good option if element is non-clickable/blocked)

example: (iframe window element)

![er1.jpg](images/er1.png)


### bookmarklet code version:
(sometimes may doesn't work in iframe window elements)
```
javascript:(function(){if(window.rmv_init)return;window.rmv_init=true;let a=null,h=[];const st=document.createElement('style');st.innerHTML='.rmv-hl{outline:5px solid red!important;outline-offset:-5px!important;box-shadow:0 0 10px yellow!important}iframe,object,embed{pointer-events:none!important}';document.head.appendChild(st);const o=e=>{e.stopPropagation();e.preventDefault();if(a&&a!==e.target)a.classList.remove('rmv-hl');a=e.target;if(a&&a.classList)a.classList.add('rmv-hl')};const d=e=>{if(e){e.stopPropagation();e.preventDefault()}if(a&&a!==document.body&&a!==document.documentElement){if(a.tagName==='VIDEO'||a.tagName==='AUDIO')a.pause&&a.pause();const m=a.querySelectorAll?a.querySelectorAll('video,audio'):[];m.forEach(x=>x.pause&&x.pause());h.push({e:a,p:a.parentNode,n:a.nextSibling});a.remove();a=null}};const u=()=>{if(h.length>0){const{e,p,n}=h.pop();if(p){if(n&&n.parentNode===p)p.insertBefore(e,n);else p.appendChild(e)}a=e}};const k=e=>{const key=e.key.toLowerCase();if(key==='delete'||key==='backspace')d(e);else if(e.ctrlKey&&key==='z'){e.preventDefault();u()}else if(key==='q'||key==='escape')c()};const c=()=>{if(a)a.classList.remove('rmv-hl');document.removeEventListener('mouseover',o,true);document.removeEventListener('click',d,true);document.removeEventListener('keydown',k,true);st.remove();window.rmv_init=false;a=null;h=[]};document.addEventListener('mouseover',o,true);document.addEventListener('click',d,true);document.addEventListener('keydown',k,true)})();
```

example:

Google Street View - remove elements

BEFORE:

![before.jpg](images/before.png)


AFTER:   
(If you see POI icons (restaurants, shops, etc.), do not move the mouse and wait a moment, and they will disappear on their own).   
(the Google logo cannot be removed)

![er2.jpg](images/er2.png)
