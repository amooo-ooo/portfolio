<script>
    import { onMount } from 'svelte';
    import moment from 'moment-timezone';
  
    const nzst = moment().tz("Pacific/Auckland");
    let time = nzst.format('HH:mm:ss');
    let gmtOffset = nzst.format('Z');
  
    const updateTime = () => {
        const nzst = moment().tz("Pacific/Auckland");
      time = nzst.format('HH:mm:ss');
    };
  
    onMount(() => {
      updateTime();
      const interval = setInterval(updateTime, 1000);
      return () => clearInterval(interval);
    });
  </script>
  
  <div class="corner">
    <p>NZST (GMT{gmtOffset})</p>
    <p>{time}</p>
  </div>
  