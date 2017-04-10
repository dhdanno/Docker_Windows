FROM microsoft/aspnet

RUN mkdir C:\APP

# configure the new site in IIS.
RUN powershell -NoProfile -Command \
    Import-module IISAdministration; \
    New-IISSite -Name "ASPNET" -PhysicalPath C:\APP -BindingInformation "*:8000:"

# Create the IIS application pool
ADD create_app_pool.ps1 .
RUN powershell ./create_app_pool.ps1

ADD Compiled_Stuff /APP

EXPOSE 8000