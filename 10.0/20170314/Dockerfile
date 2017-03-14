FROM steenzout/odoo:10.0-base
MAINTAINER Pedro Salgado "steenzout@ymail.com"

ENV ODOO_RELEASE 20170314
ENV ODOO_SHA1SUM c47d72f499f294f079d9c3d7f96aba127c3c24e2

# Set the default config file
ENV ODOO_RC /etc/odoo/odoo.conf

# Install Odoo
RUN set -x;         curl -o odoo.deb -SL http://nightly.odoo.com/10.0/nightly/deb/odoo_10.0.20170314_all.deb         && echo "c47d72f499f294f079d9c3d7f96aba127c3c24e2 odoo.deb" | sha1sum -c -         && dpkg --force-depends -i odoo.deb         && apt-get update         && apt-get -y install -f --no-install-recommends         && rm -rf /var/lib/apt/lists/* odoo.deb

# Copy entrypoint script and Odoo configuration file
COPY "./entrypoint.sh" /
COPY "./odoo.conf" /etc/odoo/
RUN chown odoo /etc/odoo/odoo.conf

# Mount /var/lib/odoo to allow restoring filestore and /mnt/extra-addons for users addons
RUN mkdir -p /mnt/extra-addons         && chown -R odoo /mnt/extra-addons
VOLUME ["/var/lib/odoo", "/mnt/extra-addons"]

# Expose Odoo services
EXPOSE 8069 8071

# Set default user when running the container
USER odoo

ENTRYPOINT ["/entrypoint.sh"]
CMD ["odoo"]
