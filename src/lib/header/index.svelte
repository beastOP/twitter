<script lang="ts">
    import Icon from 'svelte-icons-pack/Icon.svelte';
    import RiBuildingsHome5Fill from "svelte-icons-pack/ri/RiBuildingsHome5Fill";
    import RiBuildingsHome5Line from "svelte-icons-pack/ri/RiBuildingsHome5Line";
    import RiBusinessBubbleChartFill from "svelte-icons-pack/ri/RiBusinessBubbleChartFill";
    import RiBusinessBubbleChartLine from "svelte-icons-pack/ri/RiBusinessBubbleChartLine";
    import RiCommunicationChat3Fill from "svelte-icons-pack/ri/RiCommunicationChat3Fill";
    import RiCommunicationChat3Line from "svelte-icons-pack/ri/RiCommunicationChat3Line";
    import RiSystemSearchFill from "svelte-icons-pack/ri/RiSystemSearchFill";
    import RiSystemSearchLine from "svelte-icons-pack/ri/RiSystemSearchLine";
    import RiOthersBellFill from "svelte-icons-pack/ri/RiOthersBellFill";
    import RiOthersBellLine from "svelte-icons-pack/ri/RiOthersBellLine";
    let clicked = false;
    let left = 0;
    let bottom = 0;
    let nav;
    const animationSpeed = 2000;
    function handleClick(e, id) {
        clicked = id
        left = 5-nav.getBoundingClientRect().left +e.target.getBoundingClientRect().left
        bottom = window.innerHeight -e.target.getBoundingClientRect().bottom
        setTimeout(() => {
            clicked =  false
        }, animationSpeed)
    }
</script>

<svg xmlns="http://www.w3.org/2000/svg" version="1.1">
  <defs>
    <filter id="goo">
        <feGaussianBlur in="SourceGraphic" stdDeviation="10" result="blur" />
        <feColorMatrix in="blur" type="matrix" values="1 0 0 0 0  0 1 0 0 0  0 0 1 0 0  0 0 0 20 -7" result="goo" />
    </filter>
  </defs>
</svg>

<svg width="0" height="0">
</svg>

<div class='container'>
    <div class="overlay">
        <div style={`--speed: ${animationSpeed}ms;`} class:moving={clicked == 1} on:click={(e) => !clicked && handleClick(e, 1)} class="icon">
            {#if clicked != 1}
                <Icon color="white" size="1.4em" src={RiBuildingsHome5Line} />
            {:else}
                <Icon color="white" size="1.4em" src={RiBuildingsHome5Fill} />
            {/if}
        </div>
        <div style={`--speed: ${animationSpeed}ms;`} class:moving={clicked == 2} on:click={(e) => !clicked && handleClick(e, 2)} class="icon">
            {#if clicked != 2}
                <Icon color="white" size="1.4em" src={RiSystemSearchLine} />
            {:else}
                <Icon color="white" size="1.4em" src={RiSystemSearchFill} />
            {/if}
        </div>
        <div style={`--speed: ${animationSpeed}ms;`} class:moving={clicked == 3} on:click={(e) => !clicked && handleClick(e, 3)} class="icon">
            {#if clicked != 3}
                <Icon color="white" size="1.4em" src={RiBusinessBubbleChartLine} />
            {:else}
                <Icon color="white" size="1.4em" src={RiBusinessBubbleChartFill} />
            {/if}
        </div>
        <div style={`--speed: ${animationSpeed}ms;`} class:moving={clicked == 4} on:click={(e) => !clicked && handleClick(e, 4)} class="icon">
            {#if clicked != 4}
                <Icon color="white" size="1.4em" src={RiOthersBellLine} />
            {:else}
                <Icon color="white" size="1.4em" src={RiOthersBellFill} />
            {/if}
        </div>
        <div style={`--speed: ${animationSpeed}ms;`} class:moving={clicked == 5} on:click={(e) => !clicked && handleClick(e, 5)} class="icon">
            {#if clicked != 5}
                <Icon color="white" size="1.4em" src={RiCommunicationChat3Line} />
            {:else}
                <Icon color="white" size="1.4em" src={RiCommunicationChat3Fill} />
            {/if}
        </div>
    </div>
    <header bind:this={nav}>
        <nav>
            <div style={`--speed: ${animationSpeed}ms;`} class:moving={clicked == 1} class="icon">
            </div>
            <div style={`--speed: ${animationSpeed}ms;`} class:moving={clicked == 2} class="icon">
            </div>
            <div style={`--speed: ${animationSpeed}ms;`} class:moving={clicked == 3} class="icon">
            </div>
            <div style={`--speed: ${animationSpeed}ms;`} class:moving={clicked == 4} class="icon">
            </div>
            <div style={`--speed: ${animationSpeed}ms;`} class:moving={clicked == 5} class="icon">
            </div>
        </nav>
        {#if clicked}<span style={`--bottom: ${bottom}px;--left: ${left}px;--speed: ${animationSpeed}ms;`}></span>{/if}
    </header>
</div>

<style>
    :root {
        --color: #1DA1F2
    }

    .container {
        width: 100vw;
        height: 60px;
        position: fixed;
        bottom: 0;
        background: var(--color);
        padding-top: 5px;
    }

    header {
        /* width: 100%; */
        height: 100%;
        filter: url('#goo');
    }

    nav, .overlay {
        height: 100%;
        width: 80vw;
        position: absolute;
        left: 10vw;
        background: var(--color);
        display: flex;
        justify-content: space-between;
        padding: 0 1rem 5px 1rem;
        align-items: center;
    }

    .overlay {
        z-index: 50;
    }

    .icon {
        background: var(--color);
        width: 40px;
        height: 40px;
        display: flex;
        justify-content: center;
        align-items: center;
        border-radius: 50%;
        z-index: 50;
    }

    header span {
        position: absolute;
        background: var(--color);
        height: 40px;
        width: 10px;
        left: calc(var(--left));
        bottom: calc(var(--bottom)+50px);
        animation: gs calc(var(--speed)) cubic-bezier(0.18,0.89,0.32,1.27);
        transform-origin: bottom;
        z-index: 0;
    }
    
    @keyframes gs {
        0% {
            transform: scaleY(0);
        }
        20% {
            transform: scaleY(1);
        }
        32% {
            transform: scaleX(0);
            height: 40px;
        }
        90% {
            transform: scaleX(0);
            height: 0px;
            visibility: hidden;
        }
        100% {
            transform: scale(1);
            height: 0px;
            visibility: visible;
        }
    }
    
    /* Animation */
    .moving {
        /* position: relative; */
        transform-origin: center;
        animation: mup calc(var(--speed)) cubic-bezier(0.18,0.89,0.32,1.27);
    }

    @keyframes mup {
        0% {
            transform: scale(1);
            margin-top: 0px;
        }
        25% {
            transform: scale(1);
            margin-top: -150px;
        }
        50% {
            transform: scale(0);
            margin-top: -150px;
        }
        75% {
            transform: scale(0);
            margin-top: 0px;
            visibility: hidden;
        }
        80% {
            transform: scale(1);
            margin-top: 0px;
            visibility: visible;
        }
        100% {
            transform: scale(1);
            margin-top: 0px;
            visibility: visible;
        }
    }
</style>
