# Deploy a FastAPI app to Deta Space

Sometimes you need to host an API anywhere in the web because you had this crazy idea on doing one more todo app during your insomnia but then you realize Heroku is no longer free for this.

No worries, there are several free options in the web. This project aims to show you how to deploy a FastAPI app to Deta Space.

## Setting up Deta Space

You should have the [Space CLI](https://deta.space/docs/en/build/fundamentals/space-cli/) installed.

You should get the access the token from your Deta Space settings:

```bash
space login
```

Then we create our new project (I'm calling it _fast-api-sample_ here):

```bash
space new
```

## The Spacefile

Your Spacefile should look similar to this:

```yaml
v: 0
app_name: "FAPI SAMPLE"
micros:
  - name: fastapi-sample
    src: ./
    engine: python3.9
    dev: .venv/bin/uvicorn main:app --reload
```

Remember, `main:app` refers to `main.py` file / module and `app` 

## The FastAPI app

This is the simplest FastAPI app you can get:

```python
from fastapi import FastAPI

app = FastAPI()


@app.get("/")
def read_root():
    return {"Hello": "World"}
```

Remember, you need the `requirements.txt` file with all the needed dependencies. In this case, the simpler is:

```
fastapi
```

## Deploying the app

If everything goes

```bash
space push
```

🎉  Successfully pushed your code and updated your Builder instance!
Builder instance: https://fastapisample-1-p5210071.deta.app