### jekyll M1 arm64 processor not working issue.
#### new installation with ruby 2.6.0 over the 2.6.3 version of ruby has issue with installation.
> arch -arm64 brew install ruby@2.6

#### mac ruby 버젼 변경 
#### https://jetalog.net/85
> arch -arm64 rbenv local 2.6.0
> arch -arm64 bundle install
> arch -arm64 bundle exec jekyll s   

#### https://github.com/jekyll/jekyll/issues/8576
> sudo gem uninstall sassc
> sudo gem install sassc -- --disable-march-tune-native
> sudo gem uninstall ffi
> sudo gem install ffi
> bundle update --bundler
> bundle add webrick
> bundle install --redownload

#### 서버 실행 (종료 Ctrl+C)
> bundle exec jekyll serve


#### Reference 
##### resume https://altunenes.github.io/
##### project https://ssears219.github.io/  https://github.com/ssears219/ssears219.github.io
##### design https://sdloyd.github.io/
##### design https://ruggieroguida.github.io/
##### design https://promethaes.github.io/


<!--
<div class="badge-base LI-profile-badge" data-locale="ko_KR" data-size="medium" data-theme="light" data-type="VERTICAL" data-vanity="minji-jeong-173235170" data-version="v1"><a class="badge-base__link LI-simple-link" href="https://kr.linkedin.com/in/minji-jeong-173235170?trk=profile-badge">Minji Jeong</a></div>
-->          