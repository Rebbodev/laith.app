<script lang="ts">
	import Header from '../../components/Header.svelte';
	import csspng from '../../images/css.png';
	import jspng from '../../images/javascript.png';
	import tspng from '../../images/typescript.png';
	import htmlpng from '../../images/html.png';
    import bashpng from '../../images/bash.png'
    import sveletepng from '../../images/svelte.png'
    import reactpng from '../../images/react.png'
    import mysqlpng from '../../images/mysql.png'
    import pgsqlpng from '../../images/pgsql.png'
    import scyllapng from '../../images/scylla.png'
    import nodejspng from '../../images/nodejs.png'
    import pnpmpng from '../../images/pnpm.png'
    import linuxpng from '../../images/linux.png'
    import archpng from '../../images/arch.png'
    import dockerpng from '../../images/docker.png'






	const langsArr: { name: string; image: string }[] = [
		{ name: 'Bash', image: bashpng },
		{ name: 'Javascript', image: jspng },
		{ name: 'Typescript', image: tspng },
		{ name: 'HTML', image: htmlpng },
		{ name: 'CSS', image: csspng }
	];

    const techsArr: { name: string; image: string }[] = [
		{ name: 'Svelte', image: sveletepng },
		{ name: 'React', image: reactpng },
		{ name: 'MySQL', image: mysqlpng },
		{ name: 'Javascript', image: jspng },
		{ name: 'Postgres', image: pgsqlpng },
		{ name: 'Scylla', image: scyllapng }

	];

    const toolsArr: { name: string; image: string }[] = [
		{ name: 'Nodejs', image: nodejspng},
		{ name: 'Pnpm', image: pnpmpng},
		{ name: 'Linux', image: linuxpng},
		{ name: 'Arch', image: archpng},
		{ name: 'Docker', image: dockerpng}

	];

</script>

<Header />

<div id="main-div">
	<div id="titles"> 
        <p>Languages</p>
        <p>Technologies</p>
        <p>Tools</p>
    </div>
	<div id="skills">
		<div id="langs-div">
			{#each langsArr as skill}
				<div>
					<img id={skill.name} src={skill.image} alt={skill.name} />
					<p>{skill.name}</p>
				</div>
			{/each}
		</div>
		<div id="separate" />
        <div id="techs-div">
            {#each techsArr as skill}
            <div>
                <img id={skill.name} src={skill.image} alt={skill.name} />
                <p>{skill.name}</p>
            </div>
        {/each}
        </div>
        <div id="separate" />
        <div id="tools-div">
            {#each toolsArr as skill}
            <div>
                <img id={skill.name} src={skill.image} alt={skill.name} />
                <p>{skill.name}</p>
            </div>
        {/each}
        </div>

	</div>
</div>

<style lang="scss">
	#main-div {
		margin-inline: auto;
		width: 40rem;
		padding: 15px;
		#titles {
			width: auto;
			height: 20px;
            margin-bottom: 20px;

            display: flex;
            align-items: center;
            margin-bottom: 30px;
            
            p {
                font-size: 23px;
                font-family: 'Ubuntu';
                color: rgb(124, 162, 206);
                font-weight: 700;
                letter-spacing: 1px;
                margin-right: 56px;
            }
		}
		#skills {
			display: flex;

			#separate {
				width: 2px;
				height: auto;
				background-color: rgba(255, 255, 255, 0.651);
				border-radius: 4px;
                margin-right: 24px;
			}

            #tools-div {
				height: auto;
				width: 11rem;

				div {
					width: auto;
					height: auto;
					display: flex;
					align-items: center;
					border-radius: 2px;
					padding: 4px;
					margin-bottom: 10px;

					p {
						font-weight: 700;
						letter-spacing: 1px;
						font-family: 'Poppins';
						font-size: 13px;
					}

					img {
						height: 25px;
						margin-right: 13px;
					}
                }
            }

            #techs-div {
				height: auto;
				width: 11rem;

				div {
					width: auto;
					height: auto;
					display: flex;
					align-items: center;
					border-radius: 2px;
					padding: 4px;
					margin-bottom: 10px;

					p {
						font-weight: 700;
						letter-spacing: 1px;
						font-family: 'Poppins';
						font-size: 13px;
					}

					img {
						height: 25px;
						margin-right: 13px;
					}
                }
            }

			#langs-div {
				height: auto;
				width: 11rem;

				div {
					width: auto;
					height: auto;
					display: flex;
					align-items: center;
					border-radius: 2px;
					padding: 4px;
					margin-bottom: 10px;

					p {
						font-weight: 700;
						letter-spacing: 1px;
						font-family: 'Poppins';
						font-size: 13px;
					}

					img {
						height: 25px;
						margin-right: 13px;
					}
					#Javascript {
						height: 21px;
						margin-right: 15px;
						border-radius: 3px;
					}
					#Typescript {
						height: 21px;
						margin-right: 15px;
						border-radius: 3px;
					}
				}
			}
		}
	}
</style>
