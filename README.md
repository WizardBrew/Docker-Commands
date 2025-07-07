<!DOCTYPE html><html><head><meta charset="utf-8"><title>🐳 Docker Notes & Quick Deployment Guide.md</title><style></style></head><body id="preview">
<h1 class="code-line" data-line-start=0 data-line-end=1 ><a id="_Docker_Notes__Quick_Deployment_Guide_0"></a>🐳 Docker Notes &amp; Quick Deployment Guide</h1>
<p class="has-line-data" data-line-start="2" data-line-end="3">A curated collection of Docker basics, image usage, volume mounting, and custom image build-and-push instructions — for quick reference and hands-on deployment.</p>
<hr>
<h2 class="code-line" data-line-start=6 data-line-end=7 ><a id="_Install_Docker_6"></a>📥 Install Docker</h2>
<p class="has-line-data" data-line-start="8" data-line-end="9">Download &amp; install via script:</p>
<pre><code class="has-line-data" data-line-start="11" data-line-end="13" class="language-bash">curl -fsSL https://get.docker.com -o get-docker.sh
</code></pre>
<p class="has-line-data" data-line-start="14" data-line-end="15">Or visit <a href="https://get.docker.com/">https://get.docker.com/</a> for OS-specific instructions.</p>
<hr>
<h2 class="code-line" data-line-start=18 data-line-end=19 ><a id="_Website_Hosting_with_NGINX_Basic_18"></a>🌐 Website Hosting with NGINX (Basic)</h2>
<pre><code class="has-line-data" data-line-start="21" data-line-end="25" class="language-bash">docker run -ti <span class="hljs-operator">-d</span> -p <span class="hljs-number">80</span>:<span class="hljs-number">80</span> \
  -v /tmp/website/cla:/usr/share/nginx/html \
  nginx
</code></pre>
<p class="has-line-data" data-line-start="26" data-line-end="27"><strong>Explanation:</strong></p>
<ul>
<li class="has-line-data" data-line-start="27" data-line-end="28"><code>-ti</code>: Interactive terminal session</li>
<li class="has-line-data" data-line-start="28" data-line-end="29"><code>-d</code>: Detached mode</li>
<li class="has-line-data" data-line-start="29" data-line-end="30"><code>-p 80:80</code>: Exposes port 80</li>
<li class="has-line-data" data-line-start="30" data-line-end="31"><code>-v</code>: Mounts local HTML directory into NGINX’s default web root</li>
<li class="has-line-data" data-line-start="31" data-line-end="33"><code>nginx</code>: Official image used for serving web content</li>
</ul>
<p class="has-line-data" data-line-start="33" data-line-end="34">📌 <strong>Note</strong>: <code>/tmp/website/cla</code> should contain your HTML files.</p>
<hr>
<h2 class="code-line" data-line-start=37 data-line-end=38 ><a id="_Windows_11_VM_React_UI_37"></a>💻 Windows 11 VM (React UI)</h2>
<pre><code class="has-line-data" data-line-start="40" data-line-end="45" class="language-bash">docker run <span class="hljs-operator">-d</span> --restart unless-stopped \
  --name win11react \
  -p <span class="hljs-number">3000</span>:<span class="hljs-number">3000</span> \
  blueedge/win11react:latest
</code></pre>
<hr>
<h2 class="code-line" data-line-start=48 data-line-end=49 ><a id="_Run_Ubuntu_Container_48"></a>🐧 Run Ubuntu Container</h2>
<pre><code class="has-line-data" data-line-start="51" data-line-end="53" class="language-bash">docker run -it --name Ubuntu24 ubuntu bash
</code></pre>
<hr>
<h2 class="code-line" data-line-start=56 data-line-end=57 ><a id="_Important_Docker_Commands_56"></a>⚙️ Important Docker Commands</h2>
<table class="table table-striped table-bordered">
<thead>
<tr>
<th>Command</th>
<th>Purpose</th>
</tr>
</thead>
<tbody>
<tr>
<td><code>docker run &lt;image&gt;</code></td>
<td>Pull &amp; run a container</td>
</tr>
<tr>
<td><code>docker ps</code></td>
<td>List running containers</td>
</tr>
<tr>
<td><code>docker ps -a</code></td>
<td>List all (running + stopped) containers</td>
</tr>
<tr>
<td><code>docker pull &lt;image&gt;</code></td>
<td>Pull image from Docker Hub</td>
</tr>
<tr>
<td><code>docker image ls</code></td>
<td>List all images</td>
</tr>
<tr>
<td><code>docker start &lt;container_id&gt;</code></td>
<td>Start a stopped container</td>
</tr>
<tr>
<td><code>docker stop &lt;container_id&gt;</code></td>
<td>Stop a running container</td>
</tr>
<tr>
<td><code>docker rm &lt;container_id&gt;</code></td>
<td>Remove a container</td>
</tr>
<tr>
<td><code>docker rmi &lt;image&gt;</code></td>
<td>Remove an image</td>
</tr>
<tr>
<td><code>docker exec -it &lt;id&gt; bash</code></td>
<td>Access terminal inside running container</td>
</tr>
<tr>
<td><code>docker pause &lt;id&gt;</code></td>
<td>Temporarily pause container</td>
</tr>
<tr>
<td><code>docker kill &lt;id&gt;</code></td>
<td>Kill a running container</td>
</tr>
<tr>
<td><code>docker rm -f &lt;id&gt;</code></td>
<td>Force remove a container</td>
</tr>
<tr>
<td><code>docker rmi -f &lt;image&gt;</code></td>
<td>Force remove an image</td>
</tr>
<tr>
<td><code>docker start -ai &lt;name&gt;</code></td>
<td>Start and attach interactively</td>
</tr>
</tbody>
</table>
<hr>
<h2 class="code-line" data-line-start=78 data-line-end=79 ><a id="_Nginx_Proxy_Manager__Deployment_Custom_Image_78"></a>📦 Nginx Proxy Manager – Deployment (Custom Image)</h2>
<h3 class="code-line" data-line-start=80 data-line-end=81 ><a id="_Pull__Run_Your_Image_80"></a>🔹 Pull &amp; Run Your Image</h3>
<pre><code class="has-line-data" data-line-start="83" data-line-end="89" class="language-bash">docker run <span class="hljs-operator">-d</span> --name npm \
  -p <span class="hljs-number">80</span>:<span class="hljs-number">80</span> -p <span class="hljs-number">81</span>:<span class="hljs-number">81</span> -p <span class="hljs-number">443</span>:<span class="hljs-number">443</span> \
  -v <span class="hljs-variable">$HOME</span>/npm/data:/data \
  -v <span class="hljs-variable">$HOME</span>/npm/letsencrypt:/etc/letsencrypt \
  wizdockers/nginx-proxy-manager:latest
</code></pre>
<p class="has-line-data" data-line-start="90" data-line-end="91">🌐 Visit: <code>http://&lt;your-server-ip&gt;:81</code></p>
<p class="has-line-data" data-line-start="92" data-line-end="95">🔐 <strong>Default Login</strong><br>
Email: <code><a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="8eefeae3e7e0ceebf6efe3fee2eba0ede1e3">[email&#160;protected]</a></code><br>
Password: <code>changeme</code> (you’ll be prompted to change it)</p>
<hr>
<h2 class="code-line" data-line-start=98 data-line-end=99 ><a id="_Mounting_a_Local_HTML_Folder_into_NGINX_98"></a>🧩 Mounting a Local HTML Folder into NGINX</h2>
<pre><code class="has-line-data" data-line-start="101" data-line-end="105" class="language-bash">docker run --name nginx-website -p <span class="hljs-number">80</span>:<span class="hljs-number">80</span> <span class="hljs-operator">-d</span> \
  -v ~/workspace/nginx-server:/usr/share/nginx/html \
  nginx
</code></pre>
<blockquote>
<p class="has-line-data" data-line-start="106" data-line-end="107">📝 <code>~/</code> expands to <code>/home/parvez</code>, whereas <code>/root</code> is different. Mind the path context.</p>
</blockquote>
<hr>
<h2 class="code-line" data-line-start=110 data-line-end=111 ><a id="_Build_Custom_Docker_Image_with_a_Dockerfile_110"></a>🏗️ Build Custom Docker Image with a Dockerfile</h2>
<h3 class="code-line" data-line-start=112 data-line-end=113 ><a id="Example_Basic_NGINX_Setup_112"></a>Example: Basic NGINX Setup</h3>
<pre><code class="has-line-data" data-line-start="115" data-line-end="121" class="language-Dockerfile"><span class="hljs-built_in">FROM</span> ubuntu
<span class="hljs-built_in">MAINTAINER</span> <a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="16617f6c77647274647361567963627a79797d3875797b">[email&#160;protected]</a>
<span class="hljs-built_in">RUN</span> <span class="bash">apt-get update &amp;&amp; apt-get upgrade -y
</span><span class="hljs-built_in">RUN</span> <span class="bash">apt install nginx -y
</span><span class="hljs-built_in">CMD</span> <span class="bash">[<span class="hljs-string">"echo"</span>, <span class="hljs-string">"Image Created"</span>]
</span></code></pre>
<h3 class="code-line" data-line-start=122 data-line-end=123 ><a id="Build_and_Push_to_Docker_Hub_122"></a>Build and Push to Docker Hub</h3>
<pre><code class="has-line-data" data-line-start="125" data-line-end="130" class="language-bash">docker build -t my-nginx-image .
docker login
docker tag &lt;image-id&gt; wizdockers/mydockerimage:latest
docker push wizdockers/mydockerimage
</code></pre>
<hr>
<h2 class="code-line" data-line-start=133 data-line-end=134 ><a id="_Dockerfile_Instructions_Reference_133"></a>🧠 Dockerfile Instructions Reference</h2>
<table class="table table-striped table-bordered">
<thead>
<tr>
<th>Keyword</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td><code>FROM</code></td>
<td>Base image</td>
</tr>
<tr>
<td><code>MAINTAINER</code></td>
<td>Author info <em>(deprecated)</em></td>
</tr>
<tr>
<td><code>RUN</code></td>
<td>Shell command at build time</td>
</tr>
<tr>
<td><code>CMD</code></td>
<td>Default command on container start</td>
</tr>
<tr>
<td><code>COPY</code> / <code>ADD</code></td>
<td>Transfer local files (ADD supports tar/URLs)</td>
</tr>
<tr>
<td><code>EXPOSE</code></td>
<td>Ports container listens on</td>
</tr>
<tr>
<td><code>WORKDIR</code></td>
<td>Set working directory</td>
</tr>
<tr>
<td><code>ENTRYPOINT</code></td>
<td>Default executable</td>
</tr>
<tr>
<td><code>ENV</code></td>
<td>Set environment variables</td>
</tr>
<tr>
<td><code>LABEL</code></td>
<td>Add metadata</td>
</tr>
<tr>
<td><code>VOLUME</code></td>
<td>Define persistent/shared mount points</td>
</tr>
<tr>
<td><code>ARG</code></td>
<td>Build-time variable</td>
</tr>
<tr>
<td><code>USER</code></td>
<td>Set default user</td>
</tr>
</tbody>
</table>
<hr>
<p class="has-line-data" data-line-start="153" data-line-end="154">👨‍💻 Crafted by <strong>Parvez Mustak</strong> — making Docker fast, repeatable, and hassle-free.</p>

<script data-cfasync="false" src="/cdn-cgi/scripts/5c5dd728/cloudflare-static/email-decode.min.js"></script></body></html>
