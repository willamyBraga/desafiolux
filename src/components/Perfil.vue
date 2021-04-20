<template>
    <div class="row">
        <div class="col-md-4">
            <div class="card" style="width: 18rem;">
                <img class="card-img-top" :src="user.avatar_url" alt="">
                <ul class="list-group list-group-flush">
                    <li class="list-group-item">Repositrios: <span class="badge badge-success">{{user.public_repos}}</span></li>
                    <li class="list-group-item">Localização: <span class="badge badge-primary">{{user.location}}</span></li>
                    <li class="list-group-item">Seguidores: <span class="badge badge-infor">{{user.followers}}</span></li>
                    <li class="list-group-item">Seguindo: <span class="badge badge-danger">{{user.following}}</span></li>
                </ul>
                <div class="card-body">
                    <a :href="user.html_url" class="btn btn-warning btn-black">Ver perfil</a>
                </div>
            </div>
        </div>
    </div>
</template>


<script>
export default {
    props: ["user"] 
}
</script>
