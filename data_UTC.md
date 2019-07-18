# Converter Data UTC para atual 


ULR --> Referencia https://stackoverflow.com/questions/4563272/convert-a-python-utc-datetime-to-a-local-datetime-using-only-python-standard-lib?rq=1

## Funcional: 

>import pytz

>local_tz = pytz.timezone('Europe/Moscow') # use your local timezone name here

>def utc_to_local(utc_dt):
>    local_dt = utc_dt.replace(tzinfo=pytz.utc).astimezone(local_tz)
>    return local_tz.normalize(local_dt) # .normalize might be unnecessary
    
## Final 

> import pytz
> from datetime import datetime, date
> from django.conf import settings

> def converter_utc_local(utc_dt):
>    local_tz = pytz.timezone(settings.TIME_ZONE)
>    local_dt = utc_dt.replace(tzinfo=pytz.utc).astimezone(local_tz)
>    return local_tz.normalize(local_dt)
