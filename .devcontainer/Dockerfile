FROM mcr.microsoft.com/devcontainers/base:bookworm
RUN apt update\
 && apt -y install --no-install-recommends\
    cmake\
    ninja-build\
    ccache\
    gdb
# SDL 3 deps (these can be replaced with libsdl3-dev once made official)
RUN apt -y install --no-install-recommends\
    gnome-desktop-testing \
    libasound2-dev\
    libpulse-dev\
    libaudio-dev\
    libjack-dev\
    libsndio-dev\
    libx11-dev\
    libxext-dev\
    libxrandr-dev\
    libxcursor-dev\
    libxfixes-dev\
    libxi-dev\
    libxss-dev\
    libxkbcommon-dev\
    libdrm-dev\
    libgbm-dev\
    libgl1-mesa-dev\
    libgles2-mesa-dev\
    libegl1-mesa-dev\
    libdbus-1-dev\
    libibus-1.0-dev\
    libudev-dev\
    fcitx-libs-dev\
    libpipewire-0.3-dev\
    libwayland-dev\
    libdecor-0-dev\
    liburing-dev\
    libxml2-dev
RUN apt -y install --no-install-recommends\
    libvulkan1\
    mesa-vulkan-drivers
