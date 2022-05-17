### Open Source Clone 하기

Lucene / Elasticsearch / elasticsearch-analysis-arirang / arirang-analyzer-6 / arirang.morph

git clone https://github.com/apache/lucene.git
git clone https://github.com/elastic/elasticsearch.git
git clone https://github.com/HowookJeong/elasticsearch-analysis-arirang.git
git clone https://github.com/HowookJeong/arirang-analyzer-6.git
git clone https://github.com/HowookJeong/arirang.morph.git

### jenv 설치

brew install jenv
brew tap AdoptOpenJDK/openjdk

#### Shell: zsh

echo 'export PATH="$HOME/.jenv/bin:$PATH"' >> ~/.zshrc
echo 'eval "$(jenv init -)"' >> ~/.zshrc

source ~/.zshrc

jdk version 별 설치 하기)
brew install --cask adoptopenjdk8
brew install --cask adoptopenjdk11
brew install --cask adoptopenjdk15
brew install --cask adoptopenjdk16

jenv 추가)
jenv add /Library/Java/JavaVirtualMachines/adoptopenjdk-8.jdk/Contents/Home
jenv add /Library/Java/JavaVirtualMachines/adoptopenjdk-11.jdk/Contents/Home
jenv add /Library/Java/JavaVirtualMachines/adoptopenjdk-15.jdk/Contents/Home
jenv add /Library/Java/JavaVirtualMachines/adoptopenjdk-16.jdk/Contents/Home

jenv enable-plugin export

env global 설정)
Users/henryjeong/.jenv/version

jenv global 11.0 - elasticsearch 최신 버전에서는 jdk 11 을 요구 합니다.
jenv global

jenv local 설정) - elasticsearch build 에 사용하기 때문에 github/elastic/elasticsearch 위치에서 설정 합니다.
jenv local 16
jenv local
java -version

### docker 

docker 설치


### elastic 설치

wget https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-7.17.3-darwin-x86_64.tar.gz
wget https://artifacts.elastic.co/downloads/beats/filebeat/filebeat-7.17.3-darwin-x86_64.tar.gz
wget https://artifacts.elastic.co/downloads/kibana/kibana-7.17.3-darwin-x86_64.tar.gz
wget https://artifacts.elastic.co/downloads/logstash/logstash-7.17.3-darwin-x86_64.tar.gz

tar -xvzf elasticsearch-7.17.3-darwin-x86_64.tar.gz
tar -xvzf filebeat-7.17.3-darwin-x86_64.tar.gz
tar -xvzf logstash-7.17.3-darwin-x86_64.tar.gz
tar -xvzf kibana-7.17.3-darwin-x86_64.tar.gz
