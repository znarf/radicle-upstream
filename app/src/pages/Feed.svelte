<script>
  import Layout from "../layouts/SidebarLayout.svelte";
  import RowLayout from "../layouts/helpers/Row.svelte";

  import { Icon } from "../DesignSystem";
  import ProjectCard from "../components/ProjectCard.svelte";
  import { gql } from "apollo-boost";
  import { getClient, query } from "svelte-apollo";
  import { link, push } from "svelte-spa-router";

  const GET_PROJECTS = gql`
    query Query {
      listRegistryProjects
    }
  `;

  const client = getClient();
  const projects = query(client, { query: GET_PROJECTS });
  projects.refetch();
</script>

<Layout dataCy="page">
  <RowLayout>
    <div slot="left">
      {#await $projects then result}
        <ul>
          {#each result.data.listRegistryProjects as project}
            <li class="project-card">
              <ProjectCard
                title={project}
                isRegistered={true}
                imgUrl={'https://avatars.dicebear.com/v2/jdenticon/project1.svg'}
                state={Icon.Check} />
            </li>
          {/each}
        </ul>
      {/await}
    </div>
  </RowLayout>
</Layout>
