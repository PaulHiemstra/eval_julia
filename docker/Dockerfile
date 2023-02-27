FROM continuumio/anaconda3
WORKDIR "/tmp"

# Downloading Julia manually form the site
RUN wget -q https://julialang-s3.julialang.org/bin/linux/x64/1.8/julia-1.8.5-linux-x86_64.tar.gz
RUN mkdir "/opt/julia-1.8.5"
RUN tar xzf julia-1.8.5-linux-x86_64.tar.gz -C "/opt/julia-1.8.5" --strip-components=1
RUN ln -fs /opt/julia-*/bin/julia /usr/local/bin/julia   

RUN julia -e 'import Pkg; Pkg.update()' && \
    julia -e 'import Pkg; Pkg.add("HDF5")' && \
    julia -e 'using Pkg; pkg"add IJulia";'
RUN julia -e 'using Pkg; Pkg.add.(["StatsKit", "CSV", "DataFrames", "DataFramesMeta", "Gadfly", "Plots", "XLSX", "GLM"])'