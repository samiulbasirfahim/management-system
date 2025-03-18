<script lang="ts">
	import InputContainer from '$lib/components/global/InputContainer.svelte';
	import Icon from '@iconify/svelte';

	let classes = ['primary', 'secondery', 'intermediate', 'higher'];

	let guardians = $state([
		{
			name: 'Abdul Karim',
			phone: '+8801712345678',
			avatar: 'https://i.pravatar.cc/150?img=1'
		}
	]);

	let fetched_guardians = [
		{
			name: 'Abdul Karim',
			phone: '+8801712345678',
			avatar: 'https://i.pravatar.cc/150?img=1'
		},
		{
			name: 'Fatema Begum',
			phone: '+8801812345679',
			avatar: 'https://i.pravatar.cc/150?img=2'
		},
		{
			name: 'Md. Imran Hossain',
			phone: '+8801912345680',
			avatar: 'https://i.pravatar.cc/150?img=3'
		},
		{
			name: 'Nasrin Akter',
			phone: '+8801612345681',
			avatar: 'https://i.pravatar.cc/150?img=4'
		},
		{
			name: 'Rahim Uddin',
			phone: '+8801512345682',
			avatar: 'https://i.pravatar.cc/150?img=5'
		},
		{
			name: 'Sultana Jahan',
			phone: '+8801712345683',
			avatar: 'https://i.pravatar.cc/150?img=6'
		},
		{
			name: 'Shahadat Hossain',
			phone: '+8801812345684',
			avatar: 'https://i.pravatar.cc/150?img=7'
		},
		{
			name: 'Mariam Khatun',
			phone: '+8801912345685',
			avatar: 'https://i.pravatar.cc/150?img=8'
		},
		{
			name: 'Jahangir Alam',
			phone: '+8801612345686',
			avatar: 'https://i.pravatar.cc/150?img=9'
		},
		{
			name: 'Parvin Sultana',
			phone: '+8801512345687',
			avatar: 'https://i.pravatar.cc/150?img=10'
		}
	];
</script>

<div class="flex w-full flex-col p-8 lg:flex-row">
	<div
		class="card bg-base-300 rounded-box grid grow grid-cols-1 place-items-center gap-6 p-6 sm:grid-cols-2 lg:grid-cols-1 2xl:grid-cols-2"
	>
		<InputContainer name="name" label="Full name: ">
			<input type="text" name="name" class="input w-full" />
		</InputContainer>

		<InputContainer name="phone" label="Phone: ">
			<input type="number" name="phone" class="input w-full" />
		</InputContainer>

		<InputContainer
			name="address"
			label="Address: "
			class="w-full sm:col-span-2 lg:col-span-1 2xl:col-span-2"
		>
			<input type="text" name="address" class="input w-full" />
		</InputContainer>

		<ul class="bg-base-200 w-full sm:col-span-2 lg:col-span-1 2xl:col-span-2">
			<li class="p-4 pb-0 text-xs tracking-wide opacity-60">Guardians</li>
			<div
				class="list card rounded-box grid w-full grow grid-cols-1 gap-4 p-4 shadow-md sm:grid-cols-2 lg:grid-cols-1 2xl:grid-cols-2"
			>
				{#each guardians as guardian (guardian)}
					<li class="list-row bg-base-100">
						<div>
							<img
								class="rounded-box size-10"
								src={guardian.avatar}
								alt="{guardian.name}'s photo"
							/>
						</div>
						<div>
							<div>{guardian.name}</div>
							<div class="text-xs font-semibold uppercase opacity-60">{guardian.phone}</div>
						</div>
						<button class="btn btn-square btn-ghost">
							<Icon icon="fa:remove" font-size="16" />
						</button>
					</li>
				{/each}
			</div>
		</ul>
	</div>
	<div class="divider lg:divider-horizontal"></div>
	<div
		class="card bg-base-300 rounded-box grid grow grid-cols-1 gap-6 p-6 sm:grid-cols-2 lg:grid-cols-1 2xl:grid-cols-2"
	>
		<InputContainer name="name" label="Class: ">
			<select class="select">
				<option disabled selected>Class</option>
				{#each classes as cls (cls)}
					<option value={cls}>{cls}</option>
				{/each}
			</select>
		</InputContainer>

		<InputContainer name="name" label="Section: ">
			<select class="select">
				<option disabled selected>Section</option>
				{#each classes as cls (cls)}
					<option value={cls}>{cls}</option>
				{/each}
			</select>
		</InputContainer>

		<InputContainer name="name" label="Blood group: ">
			<select class="select">
				<option disabled selected>Blood group</option>
				<option value="A+">A+</option>
				<option value="A-">A-</option>
				<option value="B+">B+</option>
				<option value="B-">B-</option>
				<option value="AB+">AB+</option>
				<option value="AB-">AB-</option>
				<option value="O+">O+</option>
				<option value="O-">O-</option>
				<option value="unknown">Unknown</option>
			</select>
		</InputContainer>

		<InputContainer name="dob" label="Date of birth: ">
			<input type="date" class="input" name="dob" />
		</InputContainer>

		<InputContainer name="photo" label="Photo: ">
			<input type="file" class="file-input file-input-primary" name="photo" />
		</InputContainer>

		<InputContainer name="resident" label="Resident">
			<input type="checkbox" checked class="checkbox" />
		</InputContainer>
	</div>
</div>
