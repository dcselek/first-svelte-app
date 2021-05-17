<script>

import { Router, Route, Link } from "svelte-navigator";
import { Nav, NavItem, NavLink } from "sveltestrap";
import First from './routes/first.svelte'
import Second from './routes/second.svelte'

</script>

<Router>
  <Nav style="justify-content: center;">
    <NavItem>
      <NavLink><Link to="/">First</Link></NavLink>
    </NavItem>
    <NavItem>
      <NavLink><Link to="/second">Second</Link></NavLink>
    </NavItem>
  </Nav>

  <main>
    <Route path="/">
      <First />
    </Route>

    <Route path="/second">
      <Second />
    </Route>
  </main>
</Router>

