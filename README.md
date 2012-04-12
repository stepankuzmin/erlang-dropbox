# Erlang Dropbox REST API

## Compile

    $ make

## Quick start (client usage)

    $ erl -pa ebin -s crypto -s inets -s ssl

    1> Key = "Your App key".
    2> Secret = "Your App secret".
    3> [{"oauth_token_secret", TokenSecret}, {"oauth_token", Token}] = dropbox:request_token(Key, Secret).

Redirect user to https://www.dropbox.com/1/oauth/authorize?oauth_token=Token

    4> [{"oauth_token_secret", TokenSecret2}, {"oauth_token", Token2}, {"uid", _Uid}] = dropbox:access_token(Key, Secret, Token, TokenSecret).
    5> dropbox:account_info(Key, Secret, Token2, TokenSecret2).
