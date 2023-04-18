# Conan trial

Conan c++ package manager 를 사용해본 내용을 기록함.  
아직 [ConanCenter](https://conan.io/center/) 에 등록된 패키지가 많이 없지만, 사용하기 편한 것 같음

# How to use conan

상세 내용은 [링크](https://docs.conan.io/2/tutorial/consuming_packages/build_simple_cmake_project.html) 참조.

* [conanfile](./conanfile.txt) 준비
* conan 설치 및 conan profile 생성

```sh
$ pip install conan
$ conan profile detect --force
```

* conan 의존성 다운로드. 이때, `~/.conan2/p` 에 각 패키지의 include, lib, src, bin 이 저장된다.
  
```sh
$ conan install . --output-folder=build --build=missing
```

* cmake configure & build. 주의할 점은 `-DCMAKE_TOOLCHAIN_FILE` argument 가 없으면 의존성 패키지를 찾지 못한다. 

```sh
$ cd build
$ cmake .. -DCMAKE_TOOLCHAIN_FILE=conan_toolchain.cmake -DCMAKE_BUILD_TYPE=Release
$ make
```

# vscode 연동 방법

* vscode cmake plugin 설치
* Ctrl + Shift + P 로 팔레트 열어서 `Open Settings` 선택
* 아래와 같이 configuration args 에 `-DCMAKE_TOOLCHAIN_FILE=conan_toolchain.cmake`  & `-DCMAKE_BUILD_TYPE=Release` 추가
  
![image](https://user-images.githubusercontent.com/41066039/232982967-4be9c15d-3908-4b77-8a3a-6f40f2cc37f0.png)
