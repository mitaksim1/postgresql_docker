# PostgreSQL + Docker + Fastify + Typescript

Création du fichier **docker-compose.yml** avec les configurations nécessaires pour l'installation des bases de données PostgreSQL et Redis dans un container Docker.

## Initialisation du projet avec Fastify et Typescript
```
    npm init -y 
```

```
    npm i fastify
```

```
    npm i -D typescript @types/node
```

## Configurations post install

- Dans package.json, ajouter les lignes suivantes dans les scripts :

```
"scripts": {
    "build": "tsc -p tsconfig.json",
    "start": "node index.js"
}
```

- Initialiser le fichier de configuration Typescript.

```
    npx tsc --init
```

- Créer un fichier index.ts. Ce fichier va contenir le bloc de code permettant de démarrer le serveur.

```
    import fastify from 'fastify'

    const server = fastify()

    server.get('/ping', async (request, reply) => {
      return 'pong\n'
    })

    server.listen({ port: 8080 }, (err, address) => {
      if (err) {
        console.error(err)
        process.exit(1)
      }
      console.log(`Server listening at ${address}`)
    })
```

- Lancer la commande qui va compiler le fichier *index.ts* dans le fichier *index.js*.

```
    npm run start
```
Le message suivant doit s'afficher dans la console : *Server listening at http://127.0.0.1:8080*

- Tester le serveur avec la commande :
```
    curl localhost:8080/ping
```

