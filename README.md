# 05-starting-project
Section 5 Job Artifacts &amp; Outputs


Masi I kem kry upload dhe download actions

Tash ne folderin dist, e kemi ni fajll javascript , index me nifar kodi gjenerator qe asni her nuk asht i njejt
Po dojm me e publiku qe me mujt other jobs to use it

find dist/assets/*.js -type f -execdir echo '{}' ';'

outputs:
      script-file:

tani kjo lidhet me
   - name: Publish JS filename
        run: find dist/assets/*.js -type f -execdir echo '{}' ';'


$GITHUB_OUTPUT qeky e targeton nje fajll special nga github ne kete environment , ku output asht I shkrum
Shkruj disa te dhana ne output fajll  te menagjuar nga githubi dhe ate vedose si output per kete step. Shihe demo.yml qysh asht lidh sintaksa



Masi e banem tek jobsi build
Po dojm me e perdor edhe me e pa tek jobi deploy, kjo asht e mir me ba passing data between jobs

- name: Output filename
        run: echo "${{ needs.build.outputs.script-file }}"



Problemi me install dependencies , po merr koh pak shum
Cash
Ky duhet me kan para se me u instalu

name: Cache dependencies
        uses: actions/cache@v3
        with:
          path: ~/.npm
          key: deps-node-modules-${{ hashFiles('**/package-lock.json') }}

Ideja e ktija sht, qe kur do qe ndrrohet qeky package-lock.json ,  bahen me ni hash te ri, edhe I ban re-install. Perndryshe hash key mbeten te njejta edhe cash funksionon



Npm update
