<style>
/* These styles apply only to this page! */
    .md-content__button {
        display: none;
    }
  .md-typeset h1 {
      line-height: 0;
      margin: 0;
      margin-left: -9999px;
  }
  .quickstart-wrapper {
    min-width: 300px;
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    padding-left: -50px;
    column-gap: 50px;
    row-gap: 50px;
  }
  .quickstart-wrapper > div {
    flex: 300px;
    max-width: 300px;
  }
  .tool-img{
    box-shadow: rgba(0, 0, 0, 0.24) 0px 5px 5px;
    border-radius: 5px;
    min-width: 300px;
    max-width: 300px;
    max-height: 170px;
    min-height: 170px;
  }
  .tool-caption{
    font-family:  Roboto, Helvetica, sans-serif;
    text-align: center;
    margin-top: 10px;
    font-size:  1.2rem;
    font-weight: bold;

    /* font-size: 1.25em;
    font-weight: 400; */
    letter-spacing: -.02em;
    line-height: 1.5;
  }
  .tool-description{
    font-family:  Helvetica, sans-serif;
    text-align: center;
    margin-top: 10px;
    font-size:  0.7rem;
    font-style: oblique;
    /* font-weight: bold; */
  }
</style>


{% 
    set tools = [
        {
            "env": "IDE_URL",
            "name": "IDE",
            "image": "IDE.jpg",
            "description": "Browser-based version of Visual Studio Code. Develop in any language, install hundreeds of extensions"
        },
        {
            "env": "TERMINAL_URL",
            "name": "Terminal",
            "image": "Terminal.png",
            "description": "Full-fledged browser-based terminal with Z-shell"
        },
        {
            "env": "FILEBROWSER_URL",
            "name": "File Browser",
            "image": "Filebrowser.png",
            "description": "Browse, upload and download files and folders to and from the Workspace"
        },
        {
            "env": "CRONICLE_URL",
            "name": "Cronicle",
            "image": "Cronicle.jpg",
            "description": "Schedule jobs, manage schedules, observe and monitor executions (user/pass - admin/admin)"
        },
        {
            "env": "DBDESIGNER_URL",
            "name": "DB designer",
            "image": "dbdesigner.png",
            "description": "Visual design tool for Entity Relationship Diagrams & SQL generator"
        },
        {
            "env": "SQLITE_WEB_MAIN_URL",
            "name": "SQLite database browser (main)",
            "image": "db-main.jpg",
            "description": "Develop SQLite database with the help of WEB UI"
        },
        {
            "env": "SQLITE_WEB_TEST_URL",
            "name": "SQLite database browser (test)",
            "image": "db-test.jpg",
            "description": "Develop SQLite testing database with the help of WEB UI"
        },
        {
            "env": "SQLITE_WEB_EXAMPLE_URL",
            "name": "SQLite database browser (example)",
            "image": "db-example.jpg",
            "description": "Example SQLite database with multiple extensions"
        },
        {
            "env": "SQLITE_WEB_CUSTOM_URL",
            "name": "SQLite database browser (custom)",
            "image": "db-custom.jpg",
            "description": "Not started! Start manually with your SQLite database, i.e.  <b>sqlite_web /home/static-server/sqlite-viewer/examples/Chinook_Sqlite.sqlite --host 0.0.0.0 --port 8033</b>"
        },
        {
            "env": "SQLITE_VIEWER_URL",
            "name": "SQLite browser-based viewer",
            "image": "sqlite-viewer.jpg",
            "description": "Upload local SQLite databses, explore and query data"
        },
        {
            "env": "SQLITE_WEB_GUI_URL",
            "name": "SQLite browser-based GUI",
            "image": "sqlite-gui.jpg",
            "description": "Upload local SQLite databses, explore and query data"
        },
        {
            "env": "UNGIT_URL",
            "name": "Ungit",
            "image": "Ungit.jpg",
            "description": "Manage Git repositories and work flow using beautiful UI"
        },
        {
            "env": "STATICFS_URL",
            "name": "Static File Server",
            "image": "Static-server.png",
            "description": "Serve any static websites like a breeze"
        },
        {
            "env": "MC_URL",
            "name": "M.Commander",
            "image": "MC.jpg",
            "description": "Feature rich visual file manager with internal text viewer and editor" 
        },
        {
            "env": "HTOP_URL",
            "name": "Process monitor",
            "image": "Htop.jpg",
            "description": "Monitor running process and resource utilization"
        }
        ] 
%}


<div class="quickstart-wrapper">
  {% for tool in tools %}
    {% set tool_url = get_tool_url(tool.env) %}
    <div>
        <a href="{{ tool_url }}" target="_blank" rel="noopener noreferrer">
            <img src="{{ tool.image }}" class="tool-img"/>
        </a>
        <a href="{{ tool_url }}">
            <div class="tool-caption">{{ tool.name }}</div>
        </a>
        <div class="tool-description">{{ tool.description }}</div>
    </div>
  {% endfor %}
</div>





