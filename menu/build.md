# Builder

<!-- bootstrap -->
<lokidb-load
        dbname="appbuilder.json"
        colname="builds"
        db="{{db}}"
        col="{{col}}"
        emit="db_loaded"> </lokidb-load>

<lokidb-findmax
        receive="db_loaded"
        col="{{col}}"
        property="build"
        resultset={{latestBuild}}
        emit='{"name": "latest_build_updated", "event": {{latestBuild}}'></lokidb-findmax>



<!-- Event emitters -->

<konsol-alias name="{{_new_build_button}}">
  <konsol-button>


    <konsol-map in="{{latestBuild}}"
                f='{"project": "envoy", "build": x.build + 1, "status": "Success"}'
                out={{newBuild}}></konsol-map>


    </lokidb-insert db={{db}} col={{col}} value={{newBuild}}></lokidb-insert>
    <!-- TODO(JAVIER): the actual build -->
    <konsol-emitter emit='{"name": "latest_build_updated", "e": "{"latestBuild": {{newBuild.build}}, "status": "Success"}"}'></konsol-emitter>
  <konsol-button>
</konsol-alias>



<!-- ui -->

| Project  |   Status                                       |  Action                    |
|:---------|:------------------------------------------ ----|:---------------------------|
| Envoy    | <konsol-label receive="latest_build_updated"
                           msg="{{ event.latestBuild.status }}"</konsol-label> | {{ _new_build_button }}

