Se busca que mediante un simple comando de git se dispare la creacion de una imagen y llevarla a dockerhub

# Configurar ambiente en github - gh actions

1. crear repositorio
2. crear 2 secretos en actions secrets de github, docker user y docker password con el token de acceso de docker
3. seleccionar desde actions la creacion de imagenes con docker
4. probar build de la imagen en local
5. añadir versionamiento semantico
6. testear

# para el versionamiento semantico se puede utilizar

https://github.com/marketplace/actions/git-semantic-version?version=v4.0.3

se configura de la siguiente forma:
- name: Git Semantic Version
      uses: PaulHatch/semantic-version@v4.0.3
      with:
        major_pattern: "major:"
        minor_pattern: "feat:"
        format: "${major}.${minor}.${patch}-prerelease${increment}"
      id: version

y se utiliza:

- name: Build image
      env:
        NEW_VERSION: ${{ steps.version.outputs.version }}
      run: |
        docker build -t thxmxs/docker-graphql:$NEW_VERSION .
        docker build -t thxmxs/docker-graphql:latest .


VER docker-image.yml como ejemplo