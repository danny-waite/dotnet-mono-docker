FROM microsoft/dotnet:1.1.1-runtime

# set up network
ENV ASPNETCORE_URLS http://+:80

# set env var for packages cache
ENV DOTNET_HOSTING_OPTIMIZATION_CACHE /packagescache
ENV ASPNETCORE_CACHE_VERSION 1.1.2

# set up package cache and other tools
RUN curl -o /tmp/packagescache.tar.gz \
    https://dist.asp.net/packagecache/${ASPNETCORE_CACHE_VERSION}/debian.8-x64/aspnetcore.cache.tar.gz \
    && mkdir /packagescache && cd /packagescache \
    && tar xvf /tmp/packagescache.tar.gz \
    && rm /tmp/packagescache.tar.gz

RUN apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 3FA7E0328081BFF6A14DA29AA6A19B38D3D831EF \
	&& echo "deb http://download.mono-project.com/repo/debian wheezy-libjpeg62-compat main" | tee -a /etc/apt/sources.list.d/mono-xamarin.list \
	&& echo "deb http://download.mono-project.com/repo/debian wheezy/snapshots/4.4.2.11 main" | tee -a /etc/apt/sources.list.d/mono-xamarin.list \
	&& apt-get update \
	&& apt-get install -y mono-devel \
	&& rm -rf /var/lib/apt/lists/*
