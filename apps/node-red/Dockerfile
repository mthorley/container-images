FROM nodered/node-red:3.0.2

RUN npm install node-red-dashboard
RUN npm install node-red-contrib-better-sonos@0.1.21
RUN npm install node-red-contrib-huemagic@2.8.6
RUN npm install node-red-contrib-suncron@1.4.4
RUN npm install node-red-contrib-sunevents@2.0.3
RUN npm install node-red-contrib-tasmota@0.9.7
RUN npm install node-red-contrib-throttle@0.1.6
RUN npm install node-red-contrib-ui-artless-gauge@0.3.11
RUN npm install node-red-contrib-ui-multistate-switch@1.1.0
RUN npm install node-red-contrib-unifi@0.2.9
RUN npm install node-red-contrib-influxdb@0.6.1
RUN npm install node-red-contrib-config@1.2.1
RUN npm install passport-openidconnect
RUN npm install zenwifi-client
#- RUN npm install node-red-contrib-zen-wifi-thermostat
COPY settings.js /data/settings.js
