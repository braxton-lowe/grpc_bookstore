FROM python

RUN mkdir /service
COPY protobuffer/ /service/protobuffer/
COPY recommendations/ /service/recommendations/
WORKDIR /service/recommendations
RUN python -m pip install --upgrade pip
RUN python -m pip install -r requirements.txt
RUN python -m grpc_tools.protoc -I ../protobuffer --python_out=. \
           --grpc_python_out=. ../protobuffer/recommendations.proto

EXPOSE 50051
ENTRYPOINT [ "python", "recommendations.py" ]
