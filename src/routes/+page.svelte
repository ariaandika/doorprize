

<script lang=ts>
  const angka = ['-1','-1','-1','-1']
  
  const delay = 1000
  
  function timeout(delay: number): Promise<void> {
    return new Promise((res) => {
      setTimeout(() => {
        res()
      }, delay);
    })
  }
  
  function rand() {
    return Math.floor((Math.random() * 800) + 1000)
    // return Math.floor((Math.random() * max))
  }
  
  async function shuffle(idx: number, mul = 1) {
    const shuf = 20
    const timer = (delay / shuf) * mul
    for (let i = 0; i < timer; i++) {
      await timeout(shuf)
      angka[idx] = `${rand()}`[3]
    }
  }
  
  async function start() {
    const random = `${rand()}`
    
    shuffle(0).then( e => angka[0] = random[0] )
    shuffle(1, 2).then( e => angka[1] = random[1] )
    shuffle(2, 3).then( e => angka[2] = random[2] )
    shuffle(3, 4).then( e => angka[3] = random[3] )
    // for (let i = 0; i < angka.length; i++) {
    //   await timeout(delay)
    //   angka[i] = rand()
    // }
  }
  
</script>

<section class="min-h-screen grid place-items-center">
  
  <div class="absolute top-0 my-6">
    <h1 class="text-5xl font-bold">Doorprize HUT RI ke-78 Candi Kalasan RW XIII</h1>
    <div class="grid place-items-center my-6">
      <button class="bg-red-600 rounded px-6 py-2 font-bold text-white" on:click={start}>Start</button>
    </div>
  </div>
  
  
  
  <div class="grid [grid-template-columns:90px_90px_90px_90px] gap-80">
    
    {#each angka as a}
    
      <div>
        <span class="text-9xl">
          {#if a == "-1"} Y {:else} {a} {/if}
        </span>
      </div>
      
    {/each}
    
  </div>
  
  <div class="absolute bottom-0 font-bold text-center text-3xl mb-2">
    <div>
      Panitia HUT RI
    </div>
    <div>Powered by <span class="font-bold">BANTER</span></div>
  </div>
</section>


