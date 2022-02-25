<script>
	import Header from './header.svelte'; // svelte 파일 불러와서 html요소 배치
	import Btn from './button.svelte';

	let count = 0; // 상태값 (나는 변수라고 부르는데.. )
	const handleClick = () => {
		count += 1;
		if(count >10) {
			count = 0;
		}
	}

	let user = {loggedIn:true};
	function toggle() {
		user.loggedIn = !user.loggedIn;
	}

</script>

<Header/> <!-- 여기서 html요소 배치한다 -->

<!-- <button>그냥 버튼</button> -->
<Btn {handleClick}{count}/> <!--버튼 컴포넌트로 함수, 변수 보냄. (어떻게 사용할 지는 Btn 파일 안으로 가봐야 알 수 있음.)-->
<p>{count}</p>

{#if user.loggedIn}
	<button on:click={toggle}>
		Log out
	</button>
{/if}
{#if !user.loggedIn}
	<button on:click={toggle}>
		Log in
	</button>
{/if}