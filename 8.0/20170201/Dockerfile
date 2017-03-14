FROM steenzout/odoo:8.0-base
MAINTAINER Pedro Salgado "steenzout@ymail.com"

ENV ODOO_RELEASE 20170201
ENV ODOO_SHA1SUM 8cf7bdb08ff6191deefd83fa9cdd5ee92c2c529e

# Set the default config file
ENV OPENERP_SERVER /etc/odoo/openerp-server.conf

# Install Odoo
RUN set -x;         curl -o odoo.deb -SL http://nightly.odoo.com/8.0/nightly/deb/odoo_8.0.20170201_all.deb         && echo '8cf7bdb08ff6191deefd83fa9cdd5ee92c2c529e odoo.deb' | sha1sum -c -         && dpkg --force-depends -i odoo.deb         && apt-get update         && apt-get -y install -f --no-install-recommends         && rm -rf /var/lib/apt/lists/* odoo.deb

# Copy entrypoint script and Odoo configuration file
COPY "./entrypoint.sh" /
COPY "./openerp-server.conf" /etc/odoo/
RUN chown odoo /etc/odoo/openerp-server.conf

# Mount /var/lib/odoo to allow restoring filestore and /mnt/extra-addons for users addons
RUN mkdir -p /mnt/extra-addons         && chown -R odoo /mnt/extra-addons
VOLUME ["/var/lib/odoo", "/mnt/extra-addons"]

# Expose Odoo services
EXPOSE 8069 8071 8072

# Set default user when running the container
USER odoo

ENTRYPOINT ["/entrypoint.sh"]
CMD ["openerp-server"]
