FROM vanessa/qt-creator:base

# qt-creator:base is the base install derived from erstrom/qt
# we add openjdk here to create vanessa/qt-creator
# docker build -t vanessa/qtcreator .

USER root

WORKDIR /home/user

RUN apt-get update && apt-get install -y openjdk-8-jre build-essential && \
    wget http://web.stanford.edu/dept/cs_edu/qt-creator/qtcreator/simple-project.zip && \
    unzip simple-project.zip && chown -R user /home/user

USER user
WORKDIR /qt
