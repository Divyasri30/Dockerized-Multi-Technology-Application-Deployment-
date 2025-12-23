FROM python:3.10.19-slim AS build
ADD . /python
WORKDIR /python
RUN pip install --prefix=/aws -r requirements.txt
FROM  python:3.10.19-slim AS runtime
LABEL project="python project"
LABEL author="devopsteam"
COPY --from=build /python /python_project
COPY  --from=build /aws /usr/local
WORKDIR /python_project
EXPOSE 5001
CMD [ "python","app.py"]