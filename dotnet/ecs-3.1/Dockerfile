FROM docker.io/giddu/jenkins-inbound-agent:awscli

USER root

RUN apt-get update  \
    && apt-get install -y wget zip buildah fuse-overlayfs sudo

#RUN wget https://packages.microsoft.com/config/debian/11/packages-microsoft-prod.deb -O packages-microsoft-prod.deb \
#    && dpkg -i packages-microsoft-prod.deb \
#    && rm packages-microsoft-prod.deb

#RUN apt-get update \
#    && apt-get install -y dotnet-sdk-3.1

RUN echo '%sudo ALL=(ALL) NOPASSWD:ALL' >> /etc/sudoers
RUN usermod -aG sudo jenkins

USER jenkins

#RUN dotnet tool install --global dotnet-sonarscanner

ENV PATH "$PATH:~/.dotnet/tools"

#RUN sed -i -e 's|^#mount_program|mount_program|g' -e '/additionalimage.*/a "/var/lib/shared",' /etc/containers/storage.conf

# Set up environment variables to note that this is
# not starting with user namespace and default to
# isolate the filesystem with chroot.
ENV _BUILDAH_STARTED_IN_USERNS="" \
    BUILDAH_ISOLATION=chroot \
    STORAGE_DRIVER=vfs
