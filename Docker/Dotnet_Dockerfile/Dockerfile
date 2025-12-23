FROM mcr.microsoft.com/dotnet/sdk:9.0 AS build
ADD . /Dotnet_dir
WORKDIR /Dotnet_dir
RUN dotnet publish src/Presentation/Nop.Web -c Release -o binary_folder


FROM mcr.microsoft.com/dotnet/aspnet:9.0 AS runtime
LABEL myproject=NopCommerce
LABEL autho=Divyasri
COPY --from=build /Dotnet_dir/binary_folder /Dotnet
WORKDIR /Dotnet
EXPOSE 5000
CMD [ "dotnet","Nop.Web.dll","--urls","http://0.0.0.0:5000" ]

