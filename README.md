## jekyll M1 arm64 processor not working issue.
****
```
bundler: failed to load command: jekyll (/usr/local/bin/jekyll)
LoadError: dlopen(/Library/Ruby/Gems/2.6.0/gems/ffi-1.15.5/lib/ffi_c.bundle, 0x0009): missing compatible arch in /Library/Ruby/Gems/2.6.0/gems/ffi-1.15.5/lib/ffi_c.bundle - /Library/Ruby/Gems/2.6.0/gems/ffi-1.15.5/lib/ffi_c.bundle
```


### jekyll bundle install 후 bundle exec가 안되었을때 구글링 후 3가지 과정을 순차적으로 실행하였다. 
1. homebrew를 M1 기준으로 로재타용 homebrew 재설치
2. ruby 버젼 2.6.0 버젼 하위로 세팅 (처음 2.6.0 으로 설치하려 하였을때 실패하여 homebrew를 재설치 하였음..) 
3. sassc 부분 오류 메시지가 노출되어 sassc, ffi 재설치 후 다시 bundle 새로 빌드

****

### 1. homebrew를 M1 기준으로 로재타용 homebrew 재설치
```
# M1 homebrew 설치 세팅 
# ** 로제타용 Homebrew를 설치하기 전에 응용프로그램 들어가서 실행한 터미널(iTerm) 정보가져오기 -> 로제타를 사용하여 열기 옵션을 활성화
/bin/bash -c "$(curl -fsSL https://gist.githubusercontent.com/nrubin29/bea5aa83e8dfa91370fe83b62dad6dfa/raw/48f48f7fef21abb308e129a80b3214c2538fc611/homebrew_m1.sh)"

# M1 homebrew 설치 - shell script 호출
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

#### new installation with ruby 2.6.0 over the 2.6.3 version of ruby has issue with installation.
```
> arch -arm64 brew install ruby@2.6
```

#### [mac ruby 버젼 변경](https://jetalog.net/85)
```
> arch -arm64 rbenv local 2.6.0
> arch -arm64 bundle install
> arch -arm64 bundle exec jekyll s   
```

### 3. [Can't install Jekyll on Mac OS Big Sur (Apple Silicon M1) #8576](https://github.com/jekyll/jekyll/issues/8576)
`
FFI::NotFoundError: Function 'libsass_version' not found in [/Library/Ruby/Gems/2.6.0/gems/sassc-2.4.0/lib/sassc/libsass.bundle]
`
```
> sudo gem uninstall sassc
> sudo gem install sassc -- --disable-march-tune-native
> sudo gem uninstall ffi
> sudo gem install ffi
> bundle update --bundler
> bundle add webrick
> bundle install --redownload
```

## 빌드 & 로컬 서버 실행 (종료 Ctrl+C)
```
> bundle exec jekyll serve
```

## 화면 호출
```
Browse to http://localhost:4000/
```

## Jekyll Reference 
- 로제타 homebrew 재설치 https://chanho-yoon.github.io/silicon%20mac/m1-homebrew/
- M1 Jekyll 설치 https://unluckyjung.github.io/develop-setting/2021/01/20/Mac-Jekyll-Setting/
- Can't install Jekyll on Mac OS Big Sur (Apple Silicon M1) #8576 https://github.com/jekyll/jekyll/issues/8576
===

## Theme Reference 
- resume https://altunenes.github.io/
- project https://ssears219.github.io/  https://github.com/ssears219/ssears219.github.io
- design https://sdloyd.github.io/
- design https://ruggieroguida.github.io/
- design https://promethaes.github.io/
