FROM alpine:3.9.3
RUN echo "hello world !" > message.txt
CMD cat message.txt

# Follow this steps to flatten image:
# 
# - docker build -t nonflat .
# - docker run --name flatcontainer nonflat
# - docker export flatcontainer >> flat.tar
# - cat flat.tar | docker import - flat:latest
# Use docker history IMAGE to validate flatten layers