FROM centos:7

#RUN yum clean all                                                             \
# && yum update -y 
RUN yum install -y epel-release                                                    

RUN yum install -y python2-pip subversion httpd mod_auth_mellon git mod_wsgi   \
 httpd-devel gcc python-devel python-subvertpy mod_ssl graphviz		       \
 graphviz-python graphviz-devel

EXPOSE 80/tcp
# For when we work on SSL
# EXPOSE 443/tcp

# Get the python things
RUN pip install --upgrade pip

RUN pip install Trac==1.2.5 TracAccountManager  TracAdvancedTicketWorkflow     \
 && pip install TracChangeLog TracPrivateTickets TracWikiExtras TracXMLRPC     \
 && pip install ComponentPermissionsPlugin

# Further pip stuff
RUN pip install svn+https://trac-hacks.org/svn/breadcrumbsnavplugin/trunk/
RUN pip install svn+https://trac-hacks.org/svn/collapsibleplugin/0.12/
RUN pip install svn+https://trac-hacks.org/svn/fullblogplugin/0.11/
RUN pip install git+https://github.com/trac-hacks/trac-subtickets-plugin.git
RUN pip install svn+https://trac-hacks.org/svn/graphvizplugin/trunk/
RUN pip install svn+https://trac-hacks.org/svn/usermanagerplugin/1.2/
RUN pip install svn+https://trac-hacks.org/svn/ticketteamdispatcherplugin/0.11/
RUN pip list

# Fix Permissions
RUN find /usr/lib/python2.7/site-packages -type f | xargs chmod a+r; exit 0
RUN find /usr/lib/python2.7/site-packages -type d | xargs chmod a+rx; exit 0
RUN find /usr/lib64/python2.7/site-packages -type f | xargs chmod a+r; exit 0
RUN find /usr/lib64/python2.7/site-packages -type d | xargs chmod a+rx; exit 0

CMD /usr/sbin/httpd -DFOREGROUND
