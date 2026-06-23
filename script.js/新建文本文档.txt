const works = [
  {
    title:"Brand Identity 01",
    desc:"品牌视觉系统设计 / VI Identity",
    img:"https://picsum.photos/800/1000?1"
  },
  {
    title:"Poster Design 02",
    desc:"海报视觉设计 / Poster Art",
    img:"https://picsum.photos/800/1000?2"
  },
  {
    title:"Visual System 03",
    desc:"视觉系统设计 / Grid System",
    img:"https://picsum.photos/800/1000?3"
  },
  {
    title:"Packaging 04",
    desc:"包装设计 / Product Design",
    img:"https://picsum.photos/800/1000?4"
  },
  {
    title:"UI Concept 05",
    desc:"UI 概念设计 / Interface",
    img:"https://picsum.photos/800/1000?5"
  },
  {
    title:"Editorial 06",
    desc:"版式设计 / Editorial Layout",
    img:"https://picsum.photos/800/1000?6"
  }
];

// smooth scroll
function scrollToSection(id){
  document.getElementById(id).scrollIntoView({behavior:"smooth"});
}

// modal
function openModal(i){
  document.getElementById("modal").style.display="flex";
  document.getElementById("modalTitle").innerText = works[i].title;
  document.getElementById("modalDesc").innerText = works[i].desc;
  document.getElementById("modalImg").src = works[i].img;
}

function closeModal(){
  document.getElementById("modal").style.display="none";
}

// lazy load images
const imgs = document.querySelectorAll("img.lazy");

const observer = new IntersectionObserver(entries=>{
  entries.forEach(entry=>{
    if(entry.isIntersecting){
      const img = entry.target;
      img.src = img.dataset.src;
      observer.unobserve(img);
    }
  });
});

imgs.forEach(img=>observer.observe(img));

// reveal animation
const reveals = document.querySelectorAll(".reveal");

window.addEventListener("scroll", ()=>{
  reveals.forEach(el=>{
    const top = el.getBoundingClientRect().top;
    if(top < window.innerHeight - 100){
      el.classList.add("active");
    }
  });
});