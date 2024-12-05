FROM rust:1.83

WORKDIR /

COPY ./ /

# moldのインストール
ENV MOLD_VERSION=v2.34.1
WORKDIR /
RUN git clone https://github.com/rui314/mold.git
RUN mkdir mold/build
WORKDIR /mold/build
RUN git checkout ${MOLD_VERSION}
RUN ../install-build-deps.sh
RUN cmake -DCMAKE_BUILD_TYPE=Release -DCMAKE_CXX_COMPILER=c++ ..
RUN cmake --build . -j $(nproc)
RUN cmake --install .

RUN cargo install cargo-edit cargo-watch sea-orm-cli