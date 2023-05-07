<style>
  span{
    opacity: 0%;
    position: absolute;
    padding: 0px 0px 0px 16px; 
    margin: 0;
    font-size: 72px
  }
  span.active {
    display: inline;
    opacity:100%;
  }
  p {
    float: left;
    margin: 0;
    font-size: 72px
  }
  div.container {
  position: absolute;
  height: 160px;
  margin: auto;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  font-family: montserrat , sans-serif;
  }
</style>

<div>
<div class="container"> 
  <p>
    Ian Weir is:
  </p>

  {#each [items[index]] as item (index)}
      <span in:fly="{{y: 100, duration: 1500, delay: 3000}}"  out:fly="{{y: -100, duration: 1000, delay: 3000}}" class="{item.active === true ? 'active' : ''}">{item.value}
      </span>
    {/each}
</div>

</div>

<script>
  import {fly} from 'svelte/transition'

  const items = [
                  {value: "Java", active: true}, 
                  {value: "Javascript", active: false},
                  {value: "Typescript", active: false},
                  {value: "GraphQL", active: false},
                  {value: "RESTful APIs", active: false},
                  {value: "Nodejs", active: false},
                  {value: "Jest", active: false},
                  {value: "React", active: false},
                  {value: "Angular", active: false},
                  {value: "SQL", active: false},
                  {value: "MongoDB", active: false},
                  {value: "Docker", active: false},
                ]
  let index = 0

export function nextItem() {
  items[index++].active = false
  if(index >= items.length) {
    index = 0
  }
  items[index].active = true
} 

</script>

