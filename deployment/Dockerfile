FROM databricksruntime/standard:12.2-LTS

COPY deployment/requirements.txt /tmp/requirements.txt

RUN cd /tmp && pip install -r requirements.txt
