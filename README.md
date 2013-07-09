# pyquake3

pyquake3 is a Python class (or module) that can query and execute rcon commands on a Quake 3 server.

# Features

* Simple interface
* Automatic retries
* Can access server variables
* Can send rcon commands
* Can collect player names, ping and frags.
* With an rcon password, can collect player ip addresses.

# Example

    from pyquake3 import PyQuake3
    q = PyQuake3('localhost:27960', rcon_password='hello')
    q.update()
    print 'The name of %s is %s, running map %s with %s player(s).' % (q.get_address(), q.vars['sv_hostname'], q.vars['mapname'], len(q.players))
    for player in q.players:
        print '%s with %s frags and a %sms ping' % (player.name, player.frags, player.ping)
    q.rcon_update()
    for player in q.players:
        print '%s has an address of %s' % (player.name, player.address)
    q.rcon('addbot sarge')

