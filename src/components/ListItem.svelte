<script>
    export let title;
    export let body;
      export let imgUrl;
  </script>
  
  <div class="leagueItem">
      <img src="{imgUrl}" alt="League Logo" class="leagueLogo"/>
    <h2>{title}</h2>
    <p>{body}</p>
  </div>
  
  <style>
    .leagueItem {
      border: 1px solid #ddd;
      padding: 10px;
      margin: 10px 0;
      border-radius: 5px;
      box-shadow: 2px 2px 5px rgba(0, 0, 0, 0.1);
    }
      .leagueLogo{
          height: 100px;
          width:auto;
      }
  </style>