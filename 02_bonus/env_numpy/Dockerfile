FROM python:3.6-slim
RUN pip install jupyter numpy matplotlib rise
COPY . .
RUN mkdir slides
WORKDIR /slides

# Add Tini. Tini operates as a process subreaper for jupyter. This prevents kernel crashes.
ENV TINI_VERSION v0.6.0
ADD https://github.com/krallin/tini/releases/download/${TINI_VERSION}/tini /usr/bin/tini
RUN chmod +x /usr/bin/tini
ENTRYPOINT ["/usr/bin/tini", "--"]

CMD ["jupyter", "notebook","--port=8888", "--no-browser", "--ip=0.0.0.0", "--allow-root","--NotebookApp.token='pydata'"]
#docker build -t myaccount/new_project .
#docker run -p 8888:8888 myaccount/new_project