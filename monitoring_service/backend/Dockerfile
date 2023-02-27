FROM registry.cn-hangzhou.aliyuncs.com/sonobuoy-cwx/build-image:demo

# Install requirements
RUN pip install --upgrade pip setuptools wheel
RUN pip install -r requirements.txt --verbose

# Execute script & application
ENTRYPOINT ["sh", "./bin/start.sh"]
