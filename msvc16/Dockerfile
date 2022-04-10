FROM mcr.microsoft.com/windows/servercore:20H2

LABEL maintainer="Luis Martinez de Bartolome <luism@jfrog.com>"

SHELL ["powershell.exe", "-ExecutionPolicy", "Bypass", "-Command"]

ENV chocolateyUseWindowsCompression=false \
    PYTHONIOENCODING=UTF-8

RUN iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1')); \
    $env:Path += '";C:\tools\python3;C:\tools\python3\Scripts"';
RUN choco install --yes git --version=2.35.1.2 --params '"/InstallDir:C:\tools\git"'
RUN choco install --yes cmake --version=3.23.0 --params '"/InstallDir:C:\tools\cmake"' --installargs 'ADD_CMAKE_TO_PATH=""System""'
RUN choco install --yes python3 --version=3.10.4 --params '"/InstallDir:C:\tools\python3"'

RUN choco install --yes visualstudio2019buildtools --version=16.11.11.0
RUN choco install --yes visualstudio2019-workload-vctools --version=1.0.1

RUN python -m pip install --quiet --upgrade pip; \
    python -m pip install win-unicode-console --quiet --upgrade --force-reinstall --no-cache; \
    python -m pip install conan --quiet --upgrade --force-reinstall --no-cache;

WORKDIR "C:/Users/ContainerAdministrator"
ENTRYPOINT ["cmd.exe", "C:\\Program Files (x86)\\Microsoft Visual C++ Build Tools\\vcbuildtools_msbuild.bat"]
