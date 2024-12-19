<script>
  import { Header, Footer } from '$lib/index'
  export let data
  import { onNavigate } from '$app/navigation';

onNavigate((navigation) => {
    if (!document.startViewTransition) return;

    return new Promise((resolve) => {
        document.startViewTransition(async () => {
            resolve();
            await navigation.complete;
        });
    });
});
</script>

<Header navigation={data.navigation} />

<main id="content">
  <slot />
</main>

<Footer footerItems={data.footer} />

<style>
@view-transition {
  navigation: auto;
}

::view-transition-group(name){
  animation: animatie 5s;
}
@keyframes animatie { 
0% { transform: translate(100%, 0%)}  50%{ transform: translate( 0%, 0%)}
0% { transform: translate(100%, 0%)}
}
</style>
