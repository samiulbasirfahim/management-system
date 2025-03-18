<script lang="ts">
	import InputContainer from '$lib/components/global/InputContainer.svelte';
	import Icon from '@iconify/svelte';
	import { trusted } from 'svelte/legacy';

	let classes = ['primary', 'secondery', 'intermediate', 'higher'];

	let guardians = $state([
		{
			name: 'Abdul Karim',
			phone: '+8801712345678',
			avatar: 'https://i.pravatar.cc/150?img=1',
			address: '12/A, Green Road, Dhaka'
		},
		{
			name: 'Abdul Karim',
			phone: '+8801712345678',
			avatar: 'https://i.pravatar.cc/150?img=1',
			address: '12/A, Green Road, Dhaka'
		},

		{
			name: 'Abdul Karim',
			phone: '+8801712345678',
			avatar: 'https://i.pravatar.cc/150?img=1',
			address: '12/A, Green Road, Dhaka'
		},
		{
			name: 'Abdul Karim',
			phone: '+8801712345678',
			avatar: 'https://i.pravatar.cc/150?img=1',
			address: '12/A, Green Road, Dhaka'
		},
		{
			name: 'Abdul Karim',
			phone: '+8801712345678',
			avatar: 'https://i.pravatar.cc/150?img=1',
			address: '12/A, Green Road, Dhaka'
		},
		{
			name: 'Abdul Karim',
			phone: '+8801712345678',
			avatar: 'https://i.pravatar.cc/150?img=1',
			address: '12/A, Green Road, Dhaka'
		},
		{
			name: 'Abdul Karim',
			phone: '+8801712345678',
			avatar: 'https://i.pravatar.cc/150?img=1',
			address: '12/A, Green Road, Dhaka'
		},
		{
			name: 'Abdul Karim',
			phone: '+8801712345678',
			avatar: 'https://i.pravatar.cc/150?img=1',
			address: '12/A, Green Road, Dhaka'
		},
		{
			name: 'Abdul Karim',
			phone: '+8801712345678',
			avatar: 'https://i.pravatar.cc/150?img=1',
			address: '12/A, Green Road, Dhaka'
		},
		{
			name: 'Abdul Karim',
			phone: '+8801712345678',
			avatar: 'https://i.pravatar.cc/150?img=1',
			address: '12/A, Green Road, Dhaka'
		},
		{
			name: 'Abdul Karim',
			phone: '+8801712345678',
			avatar: 'https://i.pravatar.cc/150?img=1',
			address: '12/A, Green Road, Dhaka'
		},
		{
			name: 'Abdul Karim',
			phone: '+8801712345678',
			avatar: 'https://i.pravatar.cc/150?img=1',
			address: '12/A, Green Road, Dhaka'
		},
		{
			name: 'Abdul Karim',
			phone: '+8801712345678',
			avatar: 'https://i.pravatar.cc/150?img=1',
			address: '12/A, Green Road, Dhaka'
		},
		{
			name: 'Abdul Karim',
			phone: '+8801712345678',
			avatar: 'https://i.pravatar.cc/150?img=1',
			address: '12/A, Green Road, Dhaka'
		},
		{
			name: 'Abdul Karim',
			phone: '+8801712345678',
			avatar: 'https://i.pravatar.cc/150?img=1',
			address: '12/A, Green Road, Dhaka'
		}
	]);

	let guardianForm = $state({
		name: '',
		phone: '',
		address: '',
		avatar: 'https://i.pravatar.cc/150?img=8'
	});

	let numberConflictGuardian = $state(false);

	const handleGuardianForm = () => {
		if (guardians.find((g) => g.phone === `+880${guardianForm.phone}`)) {
			numberConflictGuardian = true;
			setTimeout(() => (numberConflictGuardian = false), 5000);
			return;
		}

		guardians.push({
			...guardianForm,
			phone: '+880' + guardianForm.phone
		});
		guardianForm = {
			name: '',
			phone: '',
			address: '',
			avatar: guardianForm.avatar
		};
		document.getElementById('create-guardian-button')?.click();
	};
</script>

<div class="flex w-full flex-col p-8 lg:flex-row">
	<div class="flex items-start justify-start">
		<div
			class="card bg-base-300 rounded-box grid grow grid-cols-1 place-items-center gap-6 p-6 sm:grid-cols-2 lg:grid-cols-1 2xl:grid-cols-2"
		>
			<InputContainer name="name" label="Full name: ">
				<input type="text" name="name" class="input w-full" />
			</InputContainer>

			<InputContainer name="phone" label="Phone: ">
				<label class="input">
					+880
					<input
						type="tel"
						class="validator grow tabular-nums w-full"
						required
						pattern="[0-9]*"
						minlength="10"
						maxlength="10"
						title="Must be 10 digits"
						bind:value={guardianForm.phone}
					/>
					<p class="validator-hint">Must be 10 digits</p>
				</label>
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
					class="list card rounded-box grid max-h-60 w-full grow grid-cols-1 gap-4 overflow-y-auto p-4 sm:grid-cols-2 lg:grid-cols-1 2xl:grid-cols-2"
				>
					{#each guardians as guardian (guardian)}
						<li class="list-row bg-base-100 flex items-center justify-between">
							<div class="flex items-center justify-start">
								<div class="avatar">
									<div class="rounded-box w-16">
										<img src={guardian.avatar} alt="{guardian.name}'s photo" />
									</div>
								</div>
								<div class="ps-2">
									<div class="text-base font-semibold">{guardian.name}</div>
									<div class="text-sm font-medium uppercase">{guardian.phone}</div>
									<div class="text-xs font-light">{guardian.address}</div>
								</div>
							</div>
							<button class="btn btn-square btn-ghost">
								<Icon icon="fa:remove" font-size="16" />
							</button>
						</li>
					{/each}
				</div>
				<div class="flex flex-wrap justify-between gap-4 p-4">
					<label for="create-guardian" class="btn btn-primary">Create Guardian</label>
					<label for="find-guardian" class="btn btn-primary">Find Guardian</label>
				</div>
			</ul>
		</div>
	</div>
	<div class="divider lg:divider-horizontal"></div>
	<div class="flex items-start justify-start">
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
				<input type="file" class="file-input file-input-primary w-full" name="photo" />
			</InputContainer>

			<InputContainer name="resident" label="Resident">
				<input type="checkbox" checked class="checkbox" />
			</InputContainer>
		</div>
	</div>
</div>

<input type="checkbox" id="create-guardian" class="modal-toggle" />
<div class="modal">
	<form class="modal-box p-4" onsubmit={handleGuardianForm}>
		<h3 class="text-lg font-bold">Create Guardian</h3>
		<div class="py-4">
			<InputContainer name="name" label="Full name: ">
				<input
					type="text"
					name="name"
					required
					minlength="5"
					class="input w-full"
					bind:value={guardianForm.name}
				/>
			</InputContainer>
			<InputContainer name="phone" label="Phone: ">
				<label class="input">
					+880
					<input
						type="tel"
						class="validator grow tabular-nums"
						required
						pattern="[0-9]*"
						minlength="10"
						maxlength="10"
						title="Must be 10 digits"
						bind:value={guardianForm.phone}
					/>
					<p class="validator-hint">Must be 10 digits</p>
				</label>
			</InputContainer>

			<InputContainer name="address" label="Address: ">
				<input
					required
					minlength="10"
					type="text"
					name="address"
					class="input w-full"
					bind:value={guardianForm.address}
				/>
			</InputContainer>

			<InputContainer name="photo" label="Photo: ">
				<input type="file" class="file-input file-input-primary w-full" name="photo" />
			</InputContainer>
		</div>
		<div class="modal-action">
			{#if numberConflictGuardian}
				<div class="alert alert-error">
					<span>You cant have two guardian with same phone number.</span>
				</div>
			{/if}
			<div class="">
				<label for="create-guardian" class="btn btn-primary" id="create-guardian-button"
					>Close</label
				>
				<input class="btn btn-primary" type="submit" value="Save" />
			</div>
		</div>
	</form>
</div>

<input type="checkbox" id="find-guardian" class="modal-toggle" />
<div class="modal">
	<div class="modal-box bg-base-200 w-full p-4 sm:col-span-2 lg:col-span-1 2xl:col-span-2">
		<h3 class="text-lg font-bold">Find Guardian</h3>
		<div
			class="list card rounded-box grid max-h-[70vh] w-full grow grid-cols-1 gap-4 overflow-y-auto p-4"
		>
			{#each guardians as guardian (guardian)}
				<li class="list-row bg-base-100 flex items-center justify-between">
					<div class="flex items-center justify-start">
						<div class="avatar">
							<div class="rounded-box w-16">
								<img src={guardian.avatar} alt="{guardian.name}'s photo" />
							</div>
						</div>
						<div class="ps-2">
							<div class="text-base font-semibold">{guardian.name}</div>
							<div class="text-sm font-medium uppercase">{guardian.phone}</div>
							<div class="text-xs font-light">{guardian.address}</div>
						</div>
					</div>
					<button class="btn btn-square btn-ghost">
						<Icon icon="mdi:add-bold" font-size="26" />
					</button>
				</li>
			{/each}
		</div>
		<div class="modal-action">
			<label for="find-guardian" class="btn btn-primary">Close</label>
		</div>
	</div>
</div>
