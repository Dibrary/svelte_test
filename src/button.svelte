<script>
    export let handleClick; // App 에서 보낸 것(함수든 변수든) 을 받아올 수 있음.
    export let count;
</script>

<button on:click={handleClick}>그냥 버튼{count}</button> <!--버튼 클릭 시 함수 실행-->