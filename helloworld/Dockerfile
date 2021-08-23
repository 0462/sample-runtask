FROM python:3.8 as builder

WORKDIR /tmp
COPY ./src/requirements.txt /tmp
RUN pip install -r requirements.txt

FROM python:3.8-slim

ENV LANG C.UTF-8
ENV TZ Asia/Tokyo

COPY --from=builder /usr/local/lib/python3.8/site-packages /usr/local/lib/python3.8/site-packages

#起動用のユーザーを作成
RUN useradd -r -s /bin/false batchuser

# RUN apt-get update \
#     && apt-get clean \
#     && rm -rf /var/lib/apt/lists/*

COPY ./src /opt/app/src

USER batchuser

WORKDIR /opt/app/src

CMD ["python", "helloworld.py"]
