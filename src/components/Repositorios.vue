<template>
    <div class="card card-body mb-2">
    <div class="row">
        <div class="col-md-6"><a :href="repo.html_url" target="_blank">{{repo.name}}</a></div>
        <div class="col-md-6">
            <span class="badge badge-secondary">Star: {{ repo.stargazers_count }} </span>
            <span class="badge badge-primary">Forks: {{ repo.forks_count }}</span>
            <span class="badge badge-danger">Wath: {{ repo.watchers_count }}</span>
        </div>
    </div>
</div>
</template>

<script>
export default {
    props: ["repo"] 
}
</script>