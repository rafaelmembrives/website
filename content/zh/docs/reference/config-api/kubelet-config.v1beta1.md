---
title: Kubelet 配置 (v1beta1)
content_type: tool-reference
package: kubelet.config.k8s.io/v1beta1
auto_generated: true
---

<!--
title: Kubelet Configuration (v1beta1)
content_type: tool-reference
package: kubelet.config.k8s.io/v1beta1
auto_generated: true
-->

<!--
## Resource Types
-->
## 资源类型

- [KubeletConfiguration](#kubelet-config-k8s-io-v1beta1-KubeletConfiguration)
- [SerializedNodeConfigSource](#kubelet-config-k8s-io-v1beta1-SerializedNodeConfigSource)

## `KubeletConfiguration`     {#kubelet-config-k8s-io-v1beta1-KubeletConfiguration}

<!--
KubeletConfiguration contains the configuration for the Kubelet
-->
KubeletConfiguration 中包含 Kubelet 的配置。

<table class="table">
<thead><tr><th width="30%"><!--Field-->字段</th><th><!--Description-->描述</th></tr></thead>
<tbody>

<tr><td><code>apiVersion</code><br/>string</td><td><code>kubelet.config.k8s.io/v1beta1</code></td></tr>
<tr><td><code>kind</code><br/>string</td><td><code>KubeletConfiguration</code></td></tr>
<tr><td><code>enableServer</code> <B>[必需]</B><br/>
<code>bool</code>
</td>
<td>
   <!--enableServer enables Kubelet's secured server.
Note: Kubelet's insecure port is controlled by the readOnlyPort option.
If DynamicKubeletConfig (deprecated; default off) is on, when
dynamically updating this field, consider that
it may disrupt components that interact with the Kubelet server.
Default: true-->
  <p><code>enableServer</code> 会启用 kubelet 的安全服务器。</p>
  <p>注意：kubelet 的不安全端口由 <code>readOnlyPort</code> 选项控制。</p>
  <p>当 <code>DynamicKubeletConfig</code> （已弃用，默认为关闭）被启用时，
如果动态更新了此字段，请考虑可能会影响到与 kubelet 服务器交互的组件。</p>
  <p>默认值：<code>true</code></p>
</td>
</tr>

<tr><td><code>staticPodPath</code><br/>
<code>string</code>
</td>
<td>
   <!--staticPodPath is the path to the directory containing local (static) pods to
run, or the path to a single static pod file.
If DynamicKubeletConfig (deprecated; default off) is on, when
dynamically updating this field, consider that
the set of static pods specified at the new path may be different than the
ones the Kubelet initially started with, and this may disrupt your node.
Default: ""-->
  <p><code>staticPodPath</code> 是指向要运行的本地（静态）Pod 的目录，
或者指向某个静态 Pod 文件的路径。</p>
  <p>当 <code>DynamicKubeletConfig</code> （已弃用，默认为关闭）被启用时，
如果动态更新了此字段，请考虑新路径下所给的静态 Pod 集合可能与 kubelet
启动时所看到的集合不同，而这一差别可能会扰乱节点状态。</p>
  <p>默认值：""</p>
</td>
</tr>

<tr><td><code>syncFrequency</code><br/>
<a href="https://godoc.org/k8s.io/apimachinery/pkg/apis/meta/v1#Duration"><code>meta/v1.Duration</code></a>
</td>
<td>
   <!--syncFrequency is the max period between synchronizing running
containers and config.
If DynamicKubeletConfig (deprecated; default off) is on, when
dynamically updating this field, consider that
shortening this duration may have a negative performance impact, especially
as the number of Pods on the node increases. Alternatively, increasing this
duration will result in longer refresh times for ConfigMaps and Secrets.
Default: "1m"-->
  <p><code>syncFrequency</code> 是对运行中的容器和配置进行同步的最长周期。</p>
  <p>当 <code>DynamicKubeletConfig</code> （已弃用，默认为关闭）被启用时，
如果动态更新了此字段，请考虑缩短这一同步周期可能会带来负面的性能影响，
尤其当节点上 Pod 个数增加时。相反，增加此周期长度时可能会导致 ConfigMap、
Secret 这类资源未被及时更新。</p>
  <p>默认值："1m"</p>
</td>
</tr>

<tr><td><code>fileCheckFrequency</code><br/>
<a href="https://godoc.org/k8s.io/apimachinery/pkg/apis/meta/v1#Duration"><code>meta/v1.Duration</code></a>
</td>
<td>
   <!--fileCheckFrequency is the duration between checking config files for
new data.
If DynamicKubeletConfig (deprecated; default off) is on, when
dynamically updating this field, consider that
shortening the duration will cause the Kubelet to reload local Static Pod
configurations more frequently, which may have a negative performance impact.
Default: "20s"-->
  <p><code>fileCheckFrequency</code> 是对配置文件中新数据进行检查的时间间隔值。</p>
  <p>当 <code>DynamicKubeletConfig</code> （已弃用，默认为关闭）被启用时，
如果动态更新了此字段，请考虑缩短此时长会导致 kubelet 更为频繁地重新加载其静态 Pod 配置，
而这会带来负面的性能影响。</p>
  <p>默认值："20s"</p>
</td>
</tr>

<tr><td><code>httpCheckFrequency</code><br/>
<a href="https://godoc.org/k8s.io/apimachinery/pkg/apis/meta/v1#Duration"><code>meta/v1.Duration</code></a>
</td>
<td>
  <!--
   httpCheckFrequency is the duration between checking http for new data.
If DynamicKubeletConfig (deprecated; default off) is on, when
dynamically updating this field, consider that
shortening the duration will cause the Kubelet to poll staticPodURL more
frequently, which may have a negative performance impact.
Default: "20s"
  -->
  <p><code>httpCheckFrequency</code> 是对 HTTP 服务器上新数据进行检查的时间间隔值。</p>
  <p>当 <code>DynamicKubeletConfig</code> （已弃用，默认为关闭）被启用时，
如果动态更新了此字段，请考虑缩短此时长会导致 kubelet 更为频繁地轮询
<code>staticPodURL</code>，而这会带来负面的性能影响。</p>
  <p>默认值："20s"</p>
</td>
</tr>

<tr><td><code>staticPodURL</code><br/>
<code>string</code>
</td>
<td>
  <!--staticPodURL is the URL for accessing static pods to run.
If DynamicKubeletConfig (deprecated; default off) is on, when
dynamically updating this field, consider that
the set of static pods specified at the new URL may be different than the
ones the Kubelet initially started with, and this may disrupt your node.
Default: ""
  -->
  <p><code>staticPodURL</code> 是访问要运行的静态 Pod 的 URL 地址。
  <p>当 <code>DynamicKubeletConfig</code> （已弃用，默认为关闭）被启用时，
如果动态更新了此字段，新的 URL 上包含的静态 Pod 集合可能与 kubelet
初始启动时看到的不同，而这种差异可能会扰乱节点状态。</p>
  <p>默认值：""</p>
</td>
</tr>

<tr><td><code>staticPodURLHeader</code><br/>
<code>map[string][]string</code>
</td>
<td>
   <!--
   staticPodURLHeader is a map of slices with HTTP headers to use when accessing the podURL.
If DynamicKubeletConfig (deprecated; default off) is on, when
dynamically updating this field, consider that
it may disrupt the ability to read the latest set of static pods from StaticPodURL.
Default: nil
   -->
   <p><code>staticPodURLHeader</code>是一个由字符串组成的映射表，其中包含的 HTTP
头部信息用于访问<code>podURL</code>。</p>
  <p>当 <code>DynamicKubeletConfig</code> （已弃用，默认为关闭）被启用时，
如果动态更新了此字段，要考虑可能导致无法从<code>staticPodURL</code>
读取最新的静态 Pod 集合。</p>
  <p>默认值：nil</p>
</td>
</tr>

<tr><td><code>address</code><br/>
<code>string</code>
</td>
<td>
   <!--
   address is the IP address for the Kubelet to serve on (set to 0.0.0.0
for all interfaces).
If DynamicKubeletConfig (deprecated; default off) is on, when
dynamically updating this field, consider that
it may disrupt components that interact with the Kubelet server.
Default: &quot;0.0.0.0&quot;
   -->
   <p><code>address</code> 是 kubelet 提供服务所用的 IP 地址（设置为 0.0.0.0
使用所有网络接口提供服务）。</p>
  <p>当 <code>DynamicKubeletConfig</code> （已弃用，默认为关闭）被启用时，
如果动态更新了此字段，请考虑可能干扰与 kubelet 服务器交互的组件。</p>
  <p>默认值：&quot;0.0.0.0&quot;</p>
</td>
</tr>

<tr><td><code>port</code><br/>
<code>int32</code>
</td>
<td>
   <!--
   port is the port for the Kubelet to serve on.
The port number must be between 1 and 65535, inclusive.
If DynamicKubeletConfig (deprecated; default off) is on, when
dynamically updating this field, consider that
it may disrupt components that interact with the Kubelet server.
Default: 10250
   -->
   <p><code>port</code> 是 kubelet 用来提供服务所使用的端口号。
这一端口号必须介于 1 到 65535 之间，包含 1 和 65535。</p>
  <p>当 <code>DynamicKubeletConfig</code> （已弃用，默认为关闭）被启用时，
如果动态更新了此字段，请考虑可能干扰与 kubelet 服务器交互的组件。</p>
  <p>默认值：10250</p>
</td>
</tr>

<tr><td><code>readOnlyPort</code><br/>
<code>int32</code>
</td>
<td>
   <!--readOnlyPort is the read-only port for the Kubelet to serve on with
no authentication/authorization.
The port number must be between 1 and 65535, inclusive.
Setting this field to 0 disables the read-only service.
If DynamicKubeletConfig (deprecated; default off) is on, when
dynamically updating this field, consider that
it may disrupt components that interact with the Kubelet server.
Default: 0 (disabled)
   -->
   <p><code>readOnlyPort</code> 是 kubelet 用来提供服务所使用的只读端口号。
此端口上的服务不支持身份认证或鉴权。这一端口号必须介于 1 到 65535 之间，
包含 1 和 65535。将此字段设置为 0 会禁用只读服务。</p>
   <p>当 <code>DynamicKubeletConfig</code> （已弃用，默认为关闭）被启用时，
如果动态更新了此字段，请考虑可能干扰与 kubelet 服务器交互的组件。</p>
   <p>默认值：0（禁用）</p>
</td>
</tr>

<tr><td><code>tlsCertFile</code><br/>
<code>string</code>
</td>
<td>
   <!--tlsCertFile is the file containing x509 Certificate for HTTPS. (CA cert,
if any, concatenated after server cert). If tlsCertFile and
tlsPrivateKeyFile are not provided, a self-signed certificate
and key are generated for the public address and saved to the directory
passed to the Kubelet's --cert-dir flag.
If DynamicKubeletConfig (deprecated; default off) is on, when
dynamically updating this field, consider that
it may disrupt components that interact with the Kubelet server.
Default:&quot;quot;
  -->
  <p><code>tlsCertFile</code>是包含 HTTPS 所需要的 x509 证书的文件
（如果有 CA 证书，会串接到服务器证书之后）。如果<code>tlsCertFile</code>
和<code>tlsPrivateKeyFile</code>都没有设置，则系统会为节点的公开地址生成自签名的证书和私钥，
并将其保存到 kubelet <code>--cert-dir</code>参数所指定的目录下。</p>
  <p>当 <code>DynamicKubeletConfig</code> （已弃用，默认为关闭）被启用时，
如果动态更新了此字段，请考虑可能干扰与 kubelet 服务器交互的组件。</p>
  <p>默认值：&quot;&quot;</p>
</td>
</tr>

<tr><td><code>tlsPrivateKeyFile</code><br/>
<code>string</code>
</td>
<td>
   <!--tlsPrivateKeyFile is the file containing x509 private key matching tlsCertFile.
If DynamicKubeletConfig (deprecated; default off) is on, when
dynamically updating this field, consider that
it may disrupt components that interact with the Kubelet server.
Default: &quot;&quot;
   -->
   <p><code>tlsPrivateKeyFile</code>是一个包含与<code>tlsCertFile</code>
证书匹配的 X509 私钥的文件。</p>
  <p>当 <code>DynamicKubeletConfig</code> （已弃用，默认为关闭）被启用时，
如果动态更新了此字段，请考虑可能干扰与 kubelet 服务器交互的组件。</p>
  <p>默认值：&quot;&quot;</p>
</td>
</tr>

<tr><td><code>tlsCipherSuites</code><br/>
<code>[]string</code>
</td>
<td>
   <!--tlsCipherSuites is the list of allowed cipher suites for the server.
Values are from tls package constants (https://golang.org/pkg/crypto/tls/#pkg-constants).
If DynamicKubeletConfig (deprecated; default off) is on, when
dynamically updating this field, consider that
it may disrupt components that interact with the Kubelet server.
Default: nil
   -->
   <p><code>tlsCipherSuites</code>是一个字符串列表，其中包含服务器所接受的加密包名称。
列表中的每个值来自于<code>tls</code>包中定义的常数（https://golang.org/pkg/crypto/tls/#pkg-constants）。</p>
  <p>当 <code>DynamicKubeletConfig</code> （已弃用，默认为关闭）被启用时，
如果动态更新了此字段，请考虑可能干扰到与 kubelet 服务器交互的组件。</p>
  <p>默认值：nil</p>
</td>
</tr>

<tr><td><code>tlsMinVersion</code><br/>
<code>string</code>
</td>
<td>
   <!--tlsMinVersion is the minimum TLS version supported.
Values are from tls package constants (https://golang.org/pkg/crypto/tls/#pkg-constants).
If DynamicKubeletConfig (deprecated; default off) is on, when
dynamically updating this field, consider that
it may disrupt components that interact with the Kubelet server.
Default: &quot;&quot;
   -->
   <p><code>tlsMinVersion</code>给出所支持的最小 TLS 版本。
字段取值来自于<code>tls</code>包中的常数定义（https://golang.org/pkg/crypto/tls/#pkg-constants）。</p>
  <p>当 <code>DynamicKubeletConfig</code> （已弃用，默认为关闭）被启用时，
如果动态更新了此字段，请考虑可能干扰到与 kubelet 服务器交互的组件。</p>
  <p>默认值：&quot;&quot;</p>
</td>
</tr>

<tr><td><code>rotateCertificates</code><br/>
<code>bool</code>
</td>
<td>
   <!--rotateCertificates enables client certificate rotation. The Kubelet will request a
new certificate from the certificates.k8s.io API. This requires an approver to approve the
certificate signing requests.
If DynamicKubeletConfig (deprecated; default off) is on, when
dynamically updating this field, consider that
disabling it may disrupt the Kubelet's ability to authenticate with the API server
after the current certificate expires.
Default: false
   -->
   <p><code>rotateCertificates</code>用来启用客户端证书轮换。kubelet 会调用
<code>certificates.k8s.io</code> API 来请求新的证书。需要有一个批复人批准证书签名请求。</p>
  <p>当 <code>DynamicKubeletConfig</code> （已弃用，默认为关闭）被启用时，
如果动态更新了此字段，请考虑禁用此行为时可能导致 kubelet 无法在当前证书过期时向
API 服务器执行身份认证。</p>
  <p>默认值：false</code>
</td>
</tr>

<tr><td><code>serverTLSBootstrap</code><br/>
<code>bool</code>
</td>
<td>
   <!--serverTLSBootstrap enables server certificate bootstrap. Instead of self
signing a serving certificate, the Kubelet will request a certificate from
the 'certificates.k8s.io' API. This requires an approver to approve the
certificate signing requests (CSR). The RotateKubeletServerCertificate feature
must be enabled when setting this field.
If DynamicKubeletConfig (deprecated; default off) is on, when
dynamically updating this field, consider that
disabling it will stop the renewal of Kubelet server certificates, which can
disrupt components that interact with the Kubelet server in the long term,
due to certificate expiration.
Default: false
   -->
   <p><code>serverTLSBootstrap</code>用来启用服务器证书引导。系统不再使用自签名的服务证书，
kubelet 会调用<code>certificates.k8s.io</code> API 来请求证书。
需要有一个批复人来批准证书签名请求（CSR）。
设置此字段时，<code>RotateKubeletServerCertificate</code>特性必须被启用。</p>
  <p>当 <code>DynamicKubeletConfig</code> （已弃用，默认为关闭）被启用时，
如果动态更新了此字段，请考虑禁用此特性会导致 kubelet 的服务器证书无法被续约，
长期上这会干扰到与 kubelet 服务器交互的组件，因为证书会过期。</p>
  <p>默认值：false</p>
</td>
</tr>

<tr><td><code>authentication</code><br/>
<a href="#kubelet-config-k8s-io-v1beta1-KubeletAuthentication"><code>KubeletAuthentication</code></a>
</td>
<td>
   <!--authentication specifies how requests to the Kubelet's server are authenticated.
If DynamicKubeletConfig (deprecated; default off) is on, when
dynamically updating this field, consider that
it may disrupt components that interact with the Kubelet server.
Defaults:
  anonymous:
    enabled: false
  webhook:
    enabled: true
    cacheTTL: "2m"
   -->
   <p><code>authorization</code>设置发送给 kubelet 服务器的请求是如何进行身份认证的。</p>
  <p>当 <code>DynamicKubeletConfig</code> （已弃用，默认为关闭）被启用时，
如果动态更新了此字段，请考虑可能干扰与 kubelet 服务器交互的组件。</p>
  <p>默认值：</p>
  <pre><code>
  anonymous:
    enabled: false
  webhook:
    enabled: true
    cacheTTL: "2m"
  </code></pre>
</td>
</tr>

<tr><td><code>authorization</code><br/>
<a href="#kubelet-config-k8s-io-v1beta1-KubeletAuthorization"><code>KubeletAuthorization</code></a>
</td>
<td>
   <!--authorization specifies how requests to the Kubelet's server are authorized.
If DynamicKubeletConfig (deprecated; default off) is on, when
dynamically updating this field, consider that
it may disrupt components that interact with the Kubelet server.
Defaults:
  mode: Webhook
  webhook:
    cacheAuthorizedTTL: "5m"
    cacheUnauthorizedTTL: "30s"</td>
   -->
   <p><code>authorization</code>设置发送给 kubelet 服务器的请求是如何进行鉴权的。</p>
  <p>当 <code>DynamicKubeletConfig</code> （已弃用，默认为关闭）被启用时，
如果动态更新了此字段，请考虑可能会干扰到与 kubelet 服务器交互的组件。</p>
  <p>默认值：</p>
  <pre><code>
  mode: Webhook
  webhook:
    cacheAuthorizedTTL: "5m"
    cacheUnauthorizedTTL: "30s"
  </code></pre>
</td>
</tr>

<tr><td><code>registryPullQPS</code><br/>
<code>int32</code>
</td>
<td>
   <!--registryPullQPS is the limit of registry pulls per second.
The value must not be a negative number.
Setting it to 0 means no limit.
If DynamicKubeletConfig (deprecated; default off) is on, when
dynamically updating this field, consider that
it may impact scalability by changing the amount of traffic produced
by image pulls.
Default: 5
   -->
   <p><code>registryPullQPS</code>是每秒钟可以执行的镜像仓库拉取操作限值。
此值必须不能为负数。将其设置为 0 表示没有限值。</p>
  <p>当 <code>DynamicKubeletConfig</code> （已弃用，默认为关闭）被启用时，
如果动态更新了此字段，请考虑这类更新可能会因为镜像拉取所产生的流量变化而导致集群可扩缩能力问题。</p>
  <p>默认值：5</code>
</td>
</tr>

<tr><td><code>registryBurst</code><br/>
<code>int32</code>
</td>
<td>
   <!--registryBurst is the maximum size of bursty pulls, temporarily allows
pulls to burst to this number, while still not exceeding registryPullQPS.
The value must not be a negative number.
Only used if registryPullQPS is greater than 0.
If DynamicKubeletConfig (deprecated; default off) is on, when
dynamically updating this field, consider that
it may impact scalability by changing the amount of traffic produced
by image pulls.
Default: 10
   -->
   <p><code>registryBurst</code>是突发性镜像拉取的上限值，允许镜像拉取临时上升到所指定数量，
不过仍然不超过<code>registryPullQPS</code>所设置的约束。此值必须是非负值。
只有<code>registryPullQPS</code>参数值大于 0 时才会使用此设置。</p>
  <p>当 <code>DynamicKubeletConfig</code> （已弃用，默认为关闭）被启用时，
如果动态更新了此字段，请考虑可能因为镜像拉取所造成的流量变化，导致集群可扩缩能力受影响。</p>
  <p>默认值：10</p>
</td>
</tr>

<tr><td><code>eventRecordQPS</code><br/>
<code>int32</code>
</td>
<td>
   <!--eventRecordQPS is the maximum event creations per second. If 0, there
is no limit enforced. The value cannot be a negative number.
If DynamicKubeletConfig (deprecated; default off) is on, when
dynamically updating this field, consider that
it may impact scalability by changing the amount of traffic produced by
event creations.
Default: 5
   -->
   <p><code>eventRecordQPS</code>设置每秒钟可创建的事件个数上限。如果此值为 0，
则表示没有限制。此值不能设置为负数。</p>
  <p>当 <code>DynamicKubeletConfig</code> （已弃用，默认为关闭）被启用时，
如果动态更新了此字段，请考虑可能因为生成事件所造成的流量变化，导致集群可扩缩能力受影响。</p>
  <p>默认值：5</p>
</td>
</tr>

<tr><td><code>eventBurst</code><br/>
<code>int32</code>
</td>
<td>
   <!--eventBurst is the maximum size of a burst of event creations, temporarily
allows event creations to burst to this number, while still not exceeding
eventRecordQPS. This field canot be a negative number and it is only used
when eventRecordQPS > 0.
If DynamicKubeletConfig (deprecated; default off) is on, when
dynamically updating this field, consider that
it may impact scalability by changing the amount of traffic produced by
event creations.
Default: 10
   -->
   <p><code>eventBurst</code>是突发性事件创建的上限值，允许事件创建临时上升到所指定数量，
不过仍然不超过<code>eventRecordQPS</code>所设置的约束。此值必须是非负值，
且只有<code>eventRecordQPS</code>大于 0 时才会使用此设置。</p>
  <p>当 <code>DynamicKubeletConfig</code> （已弃用，默认为关闭）被启用时，
如果动态更新了此字段，请考虑可能因为事件创建所造成的流量变化，导致集群可扩缩能力受影响。</p>
  <p>默认值：10</p>
</td>
</tr>

<tr><td><code>enableDebuggingHandlers</code><br/>
<code>bool</code>
</td>
<td>
   <!--enableDebuggingHandlers enables server endpoints for log access
and local running of containers and commands, including the exec,
attach, logs, and portforward features.
If DynamicKubeletConfig (deprecated; default off) is on, when
dynamically updating this field, consider that
disabling it may disrupt components that interact with the Kubelet server.
Default: true
   -->
   <p><code>enableDebuggingHandlers</code>启用服务器上用来访问日志、
在本地运行容器和命令的端点，包括<code>exec</code>、<code>attach</code>、
<code>logs</code>和<code>portforward</code>等功能。</p>
  <p>当 <code>DynamicKubeletConfig</code> （已弃用，默认为关闭）被启用时，
如果动态更新了此字段，请考虑禁用此能力可能干扰到与 kubelet 服务器交互的组件。</p>
  <p>默认值：true</p>
</td>
</tr>

<tr><td><code>enableContentionProfiling</code><br/>
<code>bool</code>
</td>
<td>
   <!--enableContentionProfiling enables lock contention profiling, if enableDebuggingHandlers is true.
If DynamicKubeletConfig (deprecated; default off) is on, when
dynamically updating this field, consider that
enabling it may carry a performance impact.
Default: false
   -->
   <p><code>enableContentionProfiling</code>用于启用锁竞争性能分析，
仅用于<code>enableDebuggingHandlers</code>为<code>true</code>的场合。</p>
  <p>当 <code>DynamicKubeletConfig</code> （已弃用，默认为关闭）被启用时，
如果动态更新了此字段，请考虑启用此分析可能隐含着一定的性能影响。</p>
  <p>默认值：false</code>
</td>
</tr>

<tr><td><code>healthzPort</code><br/>
<code>int32</code>
</td>
<td>
   <!--healthzPort is the port of the localhost healthz endpoint (set to 0 to disable).
A valid number is between 1 and 65535.
If DynamicKubeletConfig (deprecated; default off) is on, when
dynamically updating this field, consider that
it may disrupt components that monitor Kubelet health.
Default: 10248
   -->
   <p><code>healthzPort</code>是本地主机上提供<code>healthz</code>端点的端口
（设置值为 0 时表示禁止）。合法值介于 1 和 65535 之间。</p>
  <p>当 <code>DynamicKubeletConfig</code> （已弃用，默认为关闭）被启用时，
如果动态更新了此字段，请考虑可能干扰到监控 kubelet 健康状况的组件。</p>
  <p>默认值：10248</p>
</td>
</tr>

<tr><td><code>healthzBindAddress</code><br/>
<code>string</code>
</td>
<td>
   <!--healthzBindAddress is the IP address for the healthz server to serve on.
If DynamicKubeletConfig (deprecated; default off) is on, when
dynamically updating this field, consider that
it may disrupt components that monitor Kubelet health.
Default: &quot;127.0.0.1&quot;
   -->
   <p><code>healthzBindAddress<code>是<code>healthz</code>服务器用来提供服务的 IP 地址。</p>
  <p>当 <code>DynamicKubeletConfig</code> （已弃用，默认为关闭）被启用时，
如果动态更新了此字段，请考虑可能影响到监测 kubelet 健康状况的组件。</p>
  <p>默认值：&quot;127.0.0.1&quot;</p>
</td>
</tr>

<tr><td><code>oomScoreAdj</code><br/>
<code>int32</code>
</td>
<td>
   <!--oomScoreAdj is The oom-score-adj value for kubelet process. Values
must be within the range [-1000, 1000].
If DynamicKubeletConfig (deprecated; default off) is on, when
dynamically updating this field, consider that
it may impact the stability of nodes under memory pressure.
Default: -999
   -->
   <p><code>oomScoreAdj</code> 是为 kubelet 进程设置的<code>oom-score-adj</code>值。
所设置的取值要在 [-1000, 1000] 范围之内。</p>
   <p>当 <code>DynamicKubeletConfig</code> （已弃用，默认为关闭）被启用时，
如果动态更新了此字段，请考虑可能影响到内存压力较大时节点的稳定性。</p>
   <p>默认值：-999</p>
</td>
</tr>

<tr><td><code>clusterDomain</code><br/>
<code>string</code>
</td>
<td>
   <!--clusterDomain is the DNS domain for this cluster. If set, kubelet will
configure all containers to search this domain in addition to the
host's search domains.
Dynamic Kubelet Config (deprecated, default disabled): Dynamically updating this field is not recommended,
as it should be kept in sync with the rest of the cluster.
Default: &quot;&quot;
   -->
   <p><code>clusterDomain</code>是集群的 DNS 域名。如果设置了此字段，kubelet
会配置所有容器，使之在搜索主机的搜索域的同时也搜索这里指定的 DNS 域。</p>
   <p><code>DynamicKubeletConfig</code> （已弃用，默认为关闭）：
不建议动态更新此字段，因为这一设置值要与整个集群中的其他组件保持一致。</p>
   <p>默认值：&quot;&quot;</p>
</td>
</tr>

<tr><td><code>clusterDNS</code><br/>
<code>[]string</code>
</td>
<td>
   <!--clusterDNS is a list of IP addresses for the cluster DNS server. If set,
kubelet will configure all containers to use this for DNS resolution
instead of the host's DNS servers.
If DynamicKubeletConfig (deprecated; default off) is on, when
dynamically updating this field, consider that
changes will only take effect on Pods created after the update. Draining
the node is recommended before changing this field.
Default: nil
  -->
  <p><code>clusterDNS</code>是集群 DNS 服务器的 IP 地址的列表。
如果设置了，kubelet 将会配置所有容器使用这里的 IP 地址而不是宿主系统上的 DNS
服务器来完成 DNS 解析。
  <p>当 <code>DynamicKubeletConfig</code> （已弃用，默认为关闭）被启用时，
如果动态更新了此字段，请考虑变更仅会对更新后创建的 Pod 起作用。建议在更改此字段之前腾空节点。</p>
  <p>默认值：nil</p>
</td>
</tr>

<tr><td><code>streamingConnectionIdleTimeout</code><br/>
<a href="https://godoc.org/k8s.io/apimachinery/pkg/apis/meta/v1#Duration"><code>meta/v1.Duration</code></a>
</td>
<td>
   <!--streamingConnectionIdleTimeout is the maximum time a streaming connection
can be idle before the connection is automatically closed.
If DynamicKubeletConfig (deprecated; default off) is on, when
dynamically updating this field, consider that
it may impact components that rely on infrequent updates over streaming
connections to the Kubelet server.
Default: &quot;4h&quot;
   -->
   <p><code>streamingConnectionIdleTimeout</code>设置流式连接在被自动关闭之前可以空闲的最长时间。</p>
   <p>当 <code>DynamicKubeletConfig</code> （已弃用，默认为关闭）被启用时，
如果动态更新了此字段，请考虑可能影响到依赖于通过与 kubelet
服务器间流式连接来接受非频繁更新事件的组件。</p>
   <p>默认值：&quot;4h&quot;</p>
</td>
</tr>

<tr><td><code>nodeStatusUpdateFrequency</code><br/>
<a href="https://godoc.org/k8s.io/apimachinery/pkg/apis/meta/v1#Duration"><code>meta/v1.Duration</code></a>
</td>
<td>
   <!--nodeStatusUpdateFrequency is the frequency that kubelet computes node
status. If node lease feature is not enabled, it is also the frequency that
kubelet posts node status to master.
Note: When node lease feature is not enabled, be cautious when changing the
constant, it must work with nodeMonitorGracePeriod in nodecontroller.
If DynamicKubeletConfig (deprecated; default off) is on, when
dynamically updating this field, consider that
it may impact node scalability, and also that the node controller's
nodeMonitorGracePeriod must be set to N*NodeStatusUpdateFrequency,
where N is the number of retries before the node controller marks
the node unhealthy.
Default: &quot;10s&quot;
   -->
   <p><code>nodeStatusUpdateFrequency</code>是 kubelet 计算节点状态的频率。
如果未启用节点租约特性，这一字段设置的也是 kubelet 向控制面投递节点状态的频率。</p>
   <p>注意：如果节点租约特性未被启用，更改此参数设置时要非常小心，
所设置的参数值必须与节点控制器的<code>nodeMonitorGracePeriod</code>协同。</p>
   <p>当 <code>DynamicKubeletConfig</code> （已弃用，默认为关闭）被启用时，
如果动态更新了此字段，请考虑变更可能影响节点的可扩缩性。还要注意节点控制器的
<code>nodeMonitorGracePeriod</code>必须设置为<code>N&lowast;nodeStatusUpdateFrequency</code>，
其中<code>N</code>是节点控制器标记节点不健康之前执行重试的次数。</p>
   <p>默认值：&quot;10s&quot;</p>
</td>
</tr>

<tr><td><code>nodeStatusReportFrequency</code><br/>
<a href="https://godoc.org/k8s.io/apimachinery/pkg/apis/meta/v1#Duration"><code>meta/v1.Duration</code></a>
</td>
<td>
   <!--nodeStatusReportFrequency is the frequency that kubelet posts node
status to master if node status does not change. Kubelet will ignore this
frequency and post node status immediately if any change is detected. It is
only used when node lease feature is enabled. nodeStatusReportFrequency's
default value is 5m. But if nodeStatusUpdateFrequency is set explicitly,
nodeStatusReportFrequency's default value will be set to
nodeStatusUpdateFrequency for backward compatibility.
Default: &quot;5m&quot;
   -->
   <p><code>nodeStatusReportFrequency</code>是节点状态未发生变化时，kubelet
向控制面更新节点状态的频率。如果节点状态发生变化，则 kubelet 会忽略这一频率设置，
立即更新节点状态。</p>
   <p>此字段仅当启用了节点租约特性时才被使用。<code>nodeStatusReportFrequency</code>
的默认值是&quot;5m&quot;。不过，如果<code>nodeStatusUpdateFrequency</code>
被显式设置了，则<code>nodeStatusReportFrequency</code>的默认值会等于
<code>nodeStatusUpdateFrequency</code>值，这是为了实现向后兼容。</p>
   <p>默认值：&quot;5m&quot;</p>
</td>
</tr>

<tr><td><code>nodeLeaseDurationSeconds</code><br/>
<code>int32</code>
</td>
<td>
   <!--nodeLeaseDurationSeconds is the duration the Kubelet will set on its corresponding Lease.
NodeLease provides an indicator of node health by having the Kubelet create and
periodically renew a lease, named after the node, in the kube-node-lease namespace.
If the lease expires, the node can be considered unhealthy.
The lease is currently renewed every 10s, per KEP-0009. In the future, the lease renewal
interval may be set based on the lease duration.
The field value must be greater than 0.
If DynamicKubeletConfig (deprecated; default off) is on, when
dynamically updating this field, consider that
decreasing the duration may reduce tolerance for issues that temporarily prevent
the Kubelet from renewing the lease (e.g. a short-lived network issue).
Default: 40
   -->
   <p><code>nodeLeaseDurationSeconds</code>是 kubelet 会在其对应的 Lease 对象上设置的时长值。
<code>NodeLease</code>让 kubelet 来在<code>kube-node-lease</code>名字空间中创建
按节点名称命名的租约并定期执行续约操作，并通过这种机制来了解节点健康状况。</p>
   <p>如果租约过期，则节点可被视作不健康。根据 KEP-0009 约定，目前的租约每 10 秒钟续约一次。
在将来，租约的续约时间间隔可能会根据租约的时长来设置。</p>
   <p>此字段的取值必须大于零。</p>
  <p>当 <code>DynamicKubeletConfig</code> （已弃用，默认为关闭）被启用时，
如果动态更新了此字段，请考虑缩短租约期限可能降低节点对那些暂时导致 kubelet
无法续约的问题的容忍度（例如，时延很短的网络问题）。</p>
  <p>默认值：40</p>
</td>
</tr>

<tr><td><code>imageMinimumGCAge</code><br/>
<a href="https://godoc.org/k8s.io/apimachinery/pkg/apis/meta/v1#Duration"><code>meta/v1.Duration</code></a>
</td>
<td>
   <!--imageMinimumGCAge is the minimum age for an unused image before it is
garbage collected. If DynamicKubeletConfig (deprecated; default off)
is on, when dynamically updating this field, consider that  it may trigger or
delay garbage collection, and may change the image overhead on the node.
Default: &quot;2m&quot;
   -->
   <p><code>imageMinimumGCAge</code>是对未使用镜像进行垃圾搜集之前允许其存在的时长。</p>
   <p>当 <code>DynamicKubeletConfig</code> （已弃用，默认为关闭）被启用时，
如果动态更新了此字段，请考虑这种变更可能触发垃圾收集或者延迟垃圾收集，
并且可能影响节点上镜像的额外开销。</p>
   <p>默认值：&quot;2m&quot;</p>
</td>
</tr>

<tr><td><code>imageGCHighThresholdPercent</code><br/>
<code>int32</code>
</td>
<td>
   <!--imageGCHighThresholdPercent is the percent of disk usage after which
image garbage collection is always run. The percent is calculated by
dividing this field value by 100, so this field must be between 0 and
100, inclusive. When specified, the value must be greater than
imageGCLowThresholdPercent.
If DynamicKubeletConfig (deprecated; default off) is on, when
dynamically updating this field, consider that
it may trigger or delay garbage collection, and may change the image overhead
on the node.
Default: 85
   -->
   <p><code>imageGCHighThresholdPercent</code>所给的是镜像的磁盘用量百分数，
一旦镜像用量超过此阈值，则镜像垃圾收集会一直运行。百分比是用这里的值除以 100
得到的，所以此字段取值必须介于 0 和 100 之间，包括 0 和 100。如果设置了此字段，
则取值必须大于<code>imageGCLowThresholdPercent</code>取值。</p>
   <p>当 <code>DynamicKubeletConfig</code> （已弃用，默认为关闭）被启用时，
如果动态更新了此字段，请考虑这种变更可能触发垃圾收集或者延迟垃圾收集，
并且可能影响节点上镜像的额外开销。</p>
   <p>默认值：85</p>
</td>
</tr>

<tr><td><code>imageGCLowThresholdPercent</code><br/>
<code>int32</code>
</td>
<td>
   <!--imageGCLowThresholdPercent is the percent of disk usage before which
image garbage collection is never run. Lowest disk usage to garbage
collect to. The percent is calculated by dividing this field value by 100,
so the field value must be between 0 and 100, inclusive. When specified, the
value must be less than imageGCHighThresholdPercent.
If DynamicKubeletConfig (deprecated; default off) is on, when
dynamically updating this field, consider that
it may trigger or delay garbage collection, and may change the image overhead
on the node.
Default: 80
   -->
   <p><code>imageGCLowThresholdPercent</code>所给的是镜像的磁盘用量百分数，
镜像用量低于此阈值时不会执行镜像垃圾收集操作。垃圾收集操作也将此作为最低磁盘用量边界。
百分比是用这里的值除以 100 得到的，所以此字段取值必须介于 0 和 100 之间，包括 0 和 100。
如果设置了此字段，则取值必须小于<code>imageGCHighThresholdPercent</code>取值。</p>
   <p>当 <code>DynamicKubeletConfig</code> （已弃用，默认为关闭）被启用时，
如果动态更新了此字段，请考虑这种变更可能触发垃圾收集或者延迟垃圾收集，
并且可能影响节点上镜像的额外开销。</p>
   <p>默认值：80</p>
</td>
</tr>

<tr><td><code>volumeStatsAggPeriod</code><br/>
<a href="https://godoc.org/k8s.io/apimachinery/pkg/apis/meta/v1#Duration"><code>meta/v1.Duration</code></a>
</td>
<td>
   <!--volumeStatsAggPeriod is the frequency for calculating and caching volume
disk usage for all pods.
If DynamicKubeletConfig (deprecated; default off) is on, when
dynamically updating this field, consider that
shortening the period may carry a performance impact.
Default: &quot;1m&quot;
   -->
   <p><code>volumeStatsAggPeriod</code>是计算和缓存所有 Pod 磁盘用量的频率。</p>
   <p>当 <code>DynamicKubeletConfig</code> （已弃用，默认为关闭）被启用时，
如果动态更新了此字段，请考虑缩短此周期长度可能产生性能影响。</p>
   <p>默认值：&quot;1m&quot;</p>
</td>
</tr>

<tr><td><code>kubeletCgroups</code><br/>
<code>string</code>
</td>
<td>
   <!--kubeletCgroups is the absolute name of cgroups to isolate the kubelet in
Dynamic Kubelet Config (deprecated): This field should not be updated without a full node
reboot. It is safest to keep this value the same as the local config.
Default: ""
   -->
   <p><code>kubeletCgroups</code>是用来隔离 kubelet 的控制组（CGroup）的绝对名称。</p>
   <p><code>DynamicKubeletConfig</code> （已弃用）：
更新此字段时需要对整个节点执行重启。最安全的做法是确保此值与本地配置相同。</p>
   <p>默认值：&quot;&quot;</p>
</td>
</tr>

<tr><td><code>systemCgroups</code><br/>
<code>string</code>
</td>
<td>
   <!--systemCgroups is absolute name of cgroups in which to place
all non-kernel processes that are not already in a container. Empty
for no container. Rolling back the flag requires a reboot.
The cgroupRoot must be specified if this field is not empty.
Dynamic Kubelet Config (deprecated): This field should not be updated without a full node
reboot. It is safest to keep this value the same as the local config.
Default: &quot;&qout;
   -->
   <p><code>systemCgroups</code>是用来放置那些未被容器化的、非内核的进程的控制组
(CGroup）的绝对名称。设置为空字符串表示没有这类容器。回滚此字段设置需要重启节点。
当此字段非空时，必须设置<code>cgroupRoot</code>字段。</p>
   <p><code>DynamicKubeletConfig</code> （已弃用）：
更新此字段时需要对整个节点执行重启。最安全的做法是确保此值与本地配置相同。</p>
   <p>默认值：&quot;&quot;</p>
</td>
</tr>

<tr><td><code>cgroupRoot</code><br/>
<code>string</code>
</td>
<td>
   <!--cgroupRoot is the root cgroup to use for pods. This is handled by the
container runtime on a best effort basis.
Dynamic Kubelet Config (deprecated): This field should not be updated without a full node
reboot. It is safest to keep this value the same as the local config.
Default: ""
   -->
   <p><code>cgroupRoot</code>是用来运行 Pod 的控制组 (CGroup）。
容器运行时会尽可能处理此字段的设置值。</p>
   <p><code>DynamicKubeletConfig</code> （已弃用）：
更新此字段时需要对整个节点执行重启。最安全的做法是确保此值与本地配置相同。</p>
   <p>默认值：&quot;&quot;</p>
</td>
</tr>

<tr><td><code>cgroupsPerQOS</code><br/>
<code>bool</code>
</td>
<td>
   <!--cgroupsPerQOS enable QoS based CGroup hierarchy: top level CGroups for QoS classes
and all Burstable and BestEffort Pods are brought up under their specific top level
QoS CGroup.
Dynamic Kubelet Config (deprecated): This field should not be updated without a full node
reboot. It is safest to keep this value the same as the local config.
Default: true
   -->
   <p><code>cgroupsPerQOS</code>用来启用基于 QoS 的控制组（CGroup）层次结构：
顶层的控制组用于不同 QoS 类，所有<code>Burstable</code>和<code>BestEffort</code> Pod
都会被放置到对应的顶级 QoS 控制组下。</p>
   <p><code>DynamicKubeletConfig</code> （已弃用）：
更新此字段时需要对整个节点执行重启。最安全的做法是确保此值与本地配置相同。</p>
   <p>默认值：true</p>
</td>
</tr>

<tr><td><code>cgroupDriver</code><br/>
<code>string</code>
</td>
<td>
   <!--cgroupDriver is the driver kubelet uses to manipulate CGroups on the host (cgroupfs
or systemd).
Dynamic Kubelet Config (deprecated): This field should not be updated without a full node
reboot. It is safest to keep this value the same as the local config.
Default: &quot;cgroupfs&quot;
   -->
   <p><code>cgroupDriver</code>是 kubelet 用来操控宿主系统上控制组 (CGroup）
的驱动程序（cgroupfs 或 systemd）。</p>
   <p><code>DynamicKubeletConfig</code> （已弃用）：
更新此字段时需要对整个节点执行重启。最安全的做法是确保此值与本地配置相同。</p>
   <p>默认值：&quot;cgroupfs&quot;</p>
</td>
</tr>

<tr><td><code>cpuManagerPolicy</code><br/>
<code>string</code>
</td>
<td>
   <!--cpuManagerPolicy is the name of the policy to use.
Requires the CPUManager feature gate to be enabled.
Dynamic Kubelet Config (deprecated): This field should not be updated without a full node
reboot. It is safest to keep this value the same as the local config.
Default: &quot;None&quot;
   -->
   <p><code>cpuManagerPolicy</code>是要使用的策略名称。需要启用<code>CPUManager</code>
特性门控。</p>
   <p><code>DynamicKubeletConfig</code> （已弃用）：
更新此字段时需要对整个节点执行重启。最安全的做法是确保此值与本地配置相同。</p>
   <p>默认值：&quot;None&quot;</p>
</td>
</tr>

<tr><td><code>cpuManagerPolicyOptions</code><br/>
<code>map[string]string</code>
</td>
<td>
   <!--cpuManagerPolicyOptions is a set of key=value which 	allows to set extra options
to fine tune the behaviour of the cpu manager policies.
Requires  both the "CPUManager" and "CPUManagerPolicyOptions" feature gates to be enabled.
Dynamic Kubelet Config (beta): This field should not be updated without a full node
reboot. It is safest to keep this value the same as the local config.
Default: nil
   -->
   <p><code>cpuManagerPolicyOptions</code>是一组<code>key=value</code>键值映射，
容许通过额外的选项来精细调整 CPU 管理器策略的行为。需要<code>CPUManager</code>和
<code>CPUManagerPolicyOptions</code>两个特性门控都被启用。</p>
   <p><code>DynamicKubeletConfig</code> （已弃用）：
更新此字段时需要对整个节点执行重启。最安全的做法是确保此值与本地配置相同。</p>
   <p>默认值：nil</p>
</td>
</tr>

<tr><td><code>cpuManagerReconcilePeriod</code><br/>
<a href="https://godoc.org/k8s.io/apimachinery/pkg/apis/meta/v1#Duration"><code>meta/v1.Duration</code></a>
</td>
<td>
   <!--cpuManagerReconcilePeriod is the reconciliation period for the CPU Manager.
Requires the CPUManager feature gate to be enabled.
If DynamicKubeletConfig (deprecated; default off) is on, when
dynamically updating this field, consider that
shortening the period may carry a performance impact.
Default: "10s"
   -->
   <p><code>cpuManagerReconcilePeriod</code>是 CPU 管理器的协调周期时长。
需要启用<code>CPUManager</code>特性门控。</p>
   <p><code>DynamicKubeletConfig</code> （已弃用）：
   <p>当 <code>DynamicKubeletConfig</code> （已弃用，默认为关闭）被启用时，
如果动态更新了此字段，请考虑缩短周期时长可能带来的性能影响。</p>
   <p>默认值：&quot;10s&quot;</p>
</td>
</tr>

<tr><td><code>memoryManagerPolicy</code><br/>
<code>string</code>
</td>
<td>
   <!--memoryManagerPolicy is the name of the policy to use by memory manager.
Requires the MemoryManager feature gate to be enabled.
Dynamic Kubelet Config (deprecated): This field should not be updated without a full node
reboot. It is safest to keep this value the same as the local config.
Default: &quot;none&quot;
   -->
   <p><code>memoryManagerPolicy</code>是内存管理器要使用的策略的名称。
要求启用<code>MemoryManager</code>特性门控。</p>
   <p><code>DynamicKubeletConfig</code> （已弃用）：
更新此字段时需要对整个节点执行重启。最安全的做法是确保此值与本地配置相同。</p>
   <p>默认值：&quot;none&quot;</p>
</td>
</tr>

<tr><td><code>topologyManagerPolicy</code><br/>
<code>string</code>
</td>
<td>
  <!--
   <p>topologyManagerPolicy is the name of the topology manager policy to use.
Valid values include:</p>
<ul>
<li><code>restricted</code>: kubelet only allows pods with optimal NUMA node alignment for
requested resources;</li>
<li><code>best-effort</code>: kubelet will favor pods with NUMA alignment of CPU and device
resources;</li>
<li><code>none</code>: kubelet has no knowledge of NUMA alignment of a pod's CPU and device resources.</li>
<li><code>single-numa-node</code>: kubelet only allows pods with a single NUMA alignment
of CPU and device resources.</li>
</ul>
<p>Policies other than &quot;none&quot; require the TopologyManager feature gate to be enabled.
Dynamic Kubelet Config (deprecated): This field should not be updated without a full node
reboot. It is safest to keep this value the same as the local config.
Default: &quot;none&quot;</p>
  -->
   <p><code>topologyManagerPolicy</code>是要使用的拓扑管理器策略名称。合法值包括：</p> 
   <ul>
    <li><code>restricted</code>：kubelet 仅接受在所请求资源上实现最佳 NUMA 对齐的 Pod。</li>
    <li><code>best-effort</code>：kubelet 会优选在 CPU 和设备资源上实现 NUMA 对齐的 Pod。</li>
    <li><code>none</code>：kubelet 不了解 Pod CPU 和设备资源 NUMA 对齐需求。</li>
    <li><code>single-numa-node</code>：kubelet 仅允许在 CPU 和设备资源上对齐到同一 NUMA 节点的 Pod。</li>
   </ul>
   <p>如果策略不是 &quot;none&quot;，则要求启用<code>TopologyManager</code>特性门控。</p>
   <p><code>DynamicKubeletConfig</code> （已弃用）：
更新此字段时需要对整个节点执行重启。最安全的做法是确保此值与本地配置相同。</p>
   <p>默认值：&quot;none&quot;</p>
</td>
</tr>

<tr><td><code>topologyManagerScope</code><br/>
<code>string</code>
</td>
<td>
   <!--
   <p>topologyManagerScope represents the scope of topology hint generation
that topology manager requests and hint providers generate. Valid values include:</p>
<ul>
<li><code>container</code>: topology policy is applied on a per-container basis.</li>
<li><code>pod</code>: topology policy is applied on a per-pod basis.</li>
</ul>
<p>&quot;pod&quot; scope requires the TopologyManager feature gate to be enabled.
Default: &quot;container&quot;</p>
   -->
   <p><code>topologyManagerScope</code>代表的是拓扑提示生成的范围，
拓扑提示信息由提示提供者生成，提供给拓扑管理器。合法值包括：</p>
   <ul>
    <li><code>container</code>：拓扑策略是按每个容器来实施的。</li>
    <li><code>pod</code>：拓扑策略是按每个 Pod 来实施的。</li>
   </ul>
   <p>&quot;pod&quot; 范围要求启用<code>TopologyManager</code>特性门控。</p>
   <p>默认值：&quot;container&quot;</p>
</td>
</tr>

<tr><td><code>qosReserved</code><br/>
<code>map[string]string</code>
</td>
<td>
   <!--qosReserved is a set of resource name to percentage pairs that specify
the minimum percentage of a resource reserved for exclusive use by the
guaranteed QoS tier.
Currently supported resources: &quot;memory&quot;
Requires the QOSReserved feature gate to be enabled.
Dynamic Kubelet Config (deprecated): This field should not be updated without a full node
reboot. It is safest to keep this value the same as the local config.
Default: nil
   -->
   <p><code>qosReserved</code>是一组从资源名称到百分比值的映射，用来为<code>Guaranteed</code>
QoS 类型的负载预留供其独占使用的资源百分比。目前支持的资源为：&quot;memory&quot;。
需要启用<code>QOSReserved</code>特性门控。</p>
   <p><code>DynamicKubeletConfig</code> （已弃用）：
更新此字段时需要对整个节点执行重启。最安全的做法是确保此值与本地配置相同。</p>
   <p>默认值：nil</p>
</td>
</tr>

<tr><td><code>runtimeRequestTimeout</code><br/>
<a href="https://godoc.org/k8s.io/apimachinery/pkg/apis/meta/v1#Duration"><code>meta/v1.Duration</code></a>
</td>
<td>
   <!--runtimeRequestTimeout is the timeout for all runtime requests except long running
requests - pull, logs, exec and attach.
If DynamicKubeletConfig (deprecated; default off) is on, when
dynamically updating this field, consider that
it may disrupt components that interact with the Kubelet server.
Default: &quot;2m&quot;
   -->
   <p><code>runtimeRequestTimeout</code>用来设置除长期运行的请求（<code>pull</code>、
<code>logs</code>、<code>exec</code>和<code>attach</code>）之外所有运行时请求的超时时长。</p>
   <p>当 <code>DynamicKubeletConfig</code> （已弃用，默认为关闭）被启用时，
如果动态更新了此字段，请考虑可能干扰与 kubelet 服务器交互的组件。</p>
   <p>默认值：&quot;2m&quot;</p>
</td>
</tr>

<tr><td><code>hairpinMode</code><br/>
<code>string</code>
</td>
<td>
   <!--p>hairpinMode specifies how the Kubelet should configure the container
bridge for hairpin packets.
Setting this flag allows endpoints in a Service to loadbalance back to
themselves if they should try to access their own Service. Values:</p-->
   <p><code>hairpinMode</code>设置 kubelet 如何为发夹模式数据包配置容器网桥。
设置此字段可以让 Service 中的端点在尝试访问自身 Service 时将服务请求路由的自身。
可选值有：</p>
   <!--
<li>&quot;promiscuous-bridge&quot;: make the container bridge promiscuous.</li>
<li>&quot;hairpin-veth&quot;:       set the hairpin flag on container veth interfaces.</li>
<li>&quot;none&quot;:               do nothing.</li>
   -->
   <ul>
    <li>&quot;promiscuous-bridge&quot;：将容器网桥设置为混杂模式。</li>
    <li>&quot;hairpin-veth&quot;：在容器的 veth 接口上设置发夹模式标记。</li>
    <li>&quot;none&quot;：什么也不做。</li>
   </ul>
   <!--Generally, one must set <code>--hairpin-mode=hairpin-veth to</code> achieve hairpin NAT,
because promiscuous-bridge assumes the existence of a container bridge named cbr0.
If DynamicKubeletConfig (deprecated; default off) is on, when
dynamically updating this field, consider that
it may require a node reboot, depending on the network plugin.
Default: &quot;promiscuous-bridge&quot;
    -->
   <p>一般而言，用户必须设置<code>--hairpin-mode=hairpin-veth</code>才能实现发夹模式的网络地址转译
（NAT），因为混杂模式的网桥要求存在一个名为<code>cbr0</code>的容器网桥。</p>
   <p>当 <code>DynamicKubeletConfig</code> （已弃用，默认为关闭）被启用时，
如果动态更新了此字段，请考虑取决于网络插件，可能需要重启节点。</p>
   <p>默认值：&quot;promiscuous-bridge&quot;</p>
</td>
</tr>

<tr><td><code>maxPods</code><br/>
<code>int32</code>
</td>
<td>
   <!--maxPods is the maximum number of Pods that can run on this Kubelet.
The value must be a non-negative integer.
If DynamicKubeletConfig (deprecated; default off) is on, when
dynamically updating this field, consider that
changes may cause Pods to fail admission on Kubelet restart, and may change
the value reported in Node.Status.Capacity[v1.ResourcePods], thus affecting
future scheduling decisions. Increasing this value may also decrease performance,
as more Pods can be packed into a single node.
Default: 110
   -->
   <p><code>maxPods</code>是此 kubelet 上课运行的 Pod 个数上限。此值必须为非负整数。</p>
   <p>当 <code>DynamicKubeletConfig</code> （已弃用，默认为关闭）被启用时，
如果动态更新了此字段，请考虑变更可能导致 kubelet 重启时 Pod 无法被准入，
而且可能改变<code>Node.status.capacity[v1.ResourcePods]</code>中报告的数值，
从而影响将来的调度决策。增大此个数值也可能会降低性能，因为会有更多的 Pod
塞到同一节点运行。</p>
   <p>默认值：110</p>
</td>
</tr>

<tr><td><code>podCIDR</code><br/>
<code>string</code>
</td>
<td>
   <!--podCIDR is the CIDR to use for pod IP addresses, only used in standalone mode.
In cluster mode, this is obtained from the control plane.
Dynamic Kubelet Config (deprecated): This field should always be set to the empty default.
It should only set for standalone Kubelets, which cannot use Dynamic Kubelet Config.
Default: &quot;&quot;
   -->
   <p><code>podCIDR</code>是用来设置 Pod IP 地址的 CIDR 值，仅用于独立部署模式。
运行于集群模式时，这一数值会从控制面获得。</p>
   <p><code>DynamicKubeletConfig</code> （已弃用）：
此字段应该总是设置为默认的空字符串值。并且仅用来设置独立运行的 kubelet，
因为这种 kubelet 模式下无法利用动态 kubelet 配置能力。</p>
   <p>默认值：&quot;&quot;</p>
</td>
</tr>

<tr><td><code>podPidsLimit</code><br/>
<code>int64</code>
</td>
<td>
   <!--podPidsLimit is the maximum number of PIDs in any pod.
If DynamicKubeletConfig (deprecated; default off) is on, when
dynamically updating this field, consider that
lowering it may prevent container processes from forking after the change.
Default: -1
   -->
   <p><code>podPidsLimit</code>是每个 Pod 中可使用的 PID 个数上限。</p>
   <p>当 <code>DynamicKubeletConfig</code> （已弃用，默认为关闭）被启用时，
如果动态更新了此字段，请考虑减小此值可能会导致变更后无法创建容器进程。</p>
   <p>默认值：-1</p>
</td>
</tr>

<tr><td><code>resolvConf</code><br/>
<code>string</code>
</td>
<td>
   <!--resolvConf is the resolver configuration file used as the basis
for the container DNS resolution configuration.
If DynamicKubeletConfig (deprecated; default off) is on, when
dynamically updating this field, consider that
changes will only take effect on Pods created after the update. Draining
the node is recommended before changing this field.
If set to the empty string, will override the default and effectively disable DNS lookups.
Default: "/etc/resolv.conf"
   -->
   <p><code>resolvConf</code>是一个域名解析配置文件，用作容器 DNS 解析配置的基础。</p>
   <p>当 <code>DynamicKubeletConfig</code> （已弃用，默认为关闭）被启用时，
如果动态更新了此字段，请考虑变更仅会对更新完成后所创建的 Pod 起作用。
建议在变更此字段之前先腾空节点。如果此值设置为空字符串，则会覆盖 DNS 解析的默认配置，
本质上相当于禁用了 DNS 查询。</p>
   <p>默认值：&quot;/etc/resolv.conf&quot;</p>
</td>
</tr>

<tr><td><code>runOnce</code><br/>
<code>bool</code>
</td>
<td>
   <!--runOnce causes the Kubelet to check the API server once for pods,
run those in addition to the pods specified by static pod files, and exit.
Default: false
   -->
   <p><code>runOnce</code>字段被设置时，kubelet 会咨询 API 服务器一次并获得 Pod 列表，
运行在静态 Pod 文件中指定的 Pod 及这里所获得的的 Pod，然后退出。</p>
   <p>默认值：false</p>
</td>
</tr>

<tr><td><code>cpuCFSQuota</code><br/>
<code>bool</code>
</td>
<td>
   <!--cpuCFSQuota enables CPU CFS quota enforcement for containers that
specify CPU limits.
If DynamicKubeletConfig (deprecated; default off) is on, when
dynamically updating this field, consider that
disabling it may reduce node stability.
Default: true
   -->
   <p><code>cpuCFSQuota</code>允许为设置了 CPU 限制的容器实施 CPU CFS 配额约束。</p>
   <p>当 <code>DynamicKubeletConfig</code> （已弃用，默认为关闭）被启用时，
如果动态更新了此字段，请考虑禁止此功能可能会降低节点稳定性。</p>
   <p>默认值：true</p>
</td>
</tr>

<tr><td><code>cpuCFSQuotaPeriod</code><br/>
<a href="https://godoc.org/k8s.io/apimachinery/pkg/apis/meta/v1#Duration"><code>meta/v1.Duration</code></a>
</td>
<td>
   <!--cpuCFSQuotaPeriod is the CPU CFS quota period value, `cpu.cfs_period_us`.
The value must be between 1 us and 1 second, inclusive.
Requires the CustomCPUCFSQuotaPeriod feature gate to be enabled.
If DynamicKubeletConfig (deprecated; default off) is on, when
dynamically updating this field, consider that
limits set for containers will result in different cpu.cfs_quota settings. This
will trigger container restarts on the node being reconfigured.
Default: &quot;100ms&quot;
   -->
   <p><code>cpuCFSQuotaPeriod</code>设置 CPU CFS 配额周期值，<code>cpu.cfs_period_us</code>。
此值需要介于 1 微秒和 1 秒之间，包含 1 微秒和 1 秒。
此功能要求启用<code>CustomCPUCFSQuotaPeriod</code>特性门控被启用。</p>
   <p>当 <code>DynamicKubeletConfig</code> （已弃用，默认为关闭）被启用时，
如果动态更新了此字段，请考虑为容器所设置的限制值可能导致<code>cpu.cfs_period_us</code>
设置发生变化。这一变化会在节点被重新配置时触发容器重启。</p>
   <p>默认值：&quot;100ms&quot;</p>
</td>
</tr>

<tr><td><code>nodeStatusMaxImages</code><br/>
<code>int32</code>
</td>
<td>
   <!--nodeStatusMaxImages caps the number of images reported in Node.status.images.
The value must be greater than -2.
Note: If -1 is specified, no cap will be applied. If 0 is specified, no image is returned.
If DynamicKubeletConfig (deprecated; default off) is on, when
dynamically updating this field, consider that
different values can be reported on node status.
Default: 50
   -->
   <p><code>nodeStatusMaxImages</code>限制<code>Node.status.images</code>中报告的镜像数量。
此值必须大于 -2。</p>
   <p>注意：如果设置为 -1，则不会对镜像数量做限制；如果设置为 0，则不会返回任何镜像。</p>
   <p>当 <code>DynamicKubeletConfig</code> （已弃用，默认为关闭）被启用时，
如果动态更新了此字段，请考虑节点状态中可能报告不同的数值。</p>
   <p>默认值：50</p>
</td>
</tr>

<tr><td><code>maxOpenFiles</code><br/>
<code>int64</code>
</td>
<td>
   <!--maxOpenFiles is Number of files that can be opened by Kubelet process.
The value must be a non-negative number.
If DynamicKubeletConfig (deprecated; default off) is on, when
dynamically updating this field, consider that
it may impact the ability of the Kubelet to interact with the node's filesystem.
Default: 1000000
   -->
   <p><code>maxOpenFiles</code>是 kubelet 进程可以打开的文件个数。此值必须不能为负数。</p>
   <p>当 <code>DynamicKubeletConfig</code> （已弃用，默认为关闭）被启用时，
如果动态更新了此字段，请考虑可能影响到 kubelet 与节点文件系统间交互的能力。</p>
   <p>默认值：1000000</p>
</td>
</tr>

<tr><td><code>contentType</code><br/>
<code>string</code>
</td>
<td>
   <!--contentType is contentType of requests sent to apiserver.
If DynamicKubeletConfig (deprecated; default off) is on, when
dynamically updating this field, consider that
it may impact the ability for the Kubelet to communicate with the API server.
If the Kubelet loses contact with the API server due to a change to this field,
the change cannot be reverted via dynamic Kubelet config.
Default: "application/vnd.kubernetes.protobuf"
   -->
   <p><code>contentType</code>是向 API 服务器发送请求时使用的内容类型。</p>
   <p>当 <code>DynamicKubeletConfig</code> （已弃用，默认为关闭）被启用时，
如果动态更新了此字段，请考虑这样做可能影响 kubelet 与 API 服务器通信的能力。
如果 kubelet 因为此字段的变更而失去与 API 服务器间的连接，
则之前所作的变更无法通过动态 kubelet 配置来实现回退。</p>
   <p>默认值：&quot;application/vnd.kubernetes.protobuf&quot;</p>
</td>
</tr>

<tr><td><code>kubeAPIQPS</code><br/>
<code>int32</code>
</td>
<td>
   <!--kubeAPIQPS is the QPS to use while talking with kubernetes apiserver.
If DynamicKubeletConfig (deprecated; default off) is on, when
dynamically updating this field, consider that
it may impact scalability by changing the amount of traffic the Kubelet
sends to the API server.
Default: 5
   -->
   <p><code>kubeAPIQPS</code>设置与 Kubernetes API 服务器通信时要使用的 QPS（每秒查询数）。</p>
   <p>当 <code>DynamicKubeletConfig</code> （已弃用，默认为关闭）被启用时，
如果动态更新了此字段，请考虑这可能因为 kubelet 与 API 服务器之间流量的变化而影响集群扩缩能力。</p>
   <p>默认值：5</p>
</td>
</tr>

<tr><td><code>kubeAPIBurst</code><br/>
<code>int32</code>
</td>
<td>
   <!--kubeAPIBurst is the burst to allow while talking with kubernetes API server.
This field cannot be a negative number.
If DynamicKubeletConfig (deprecated; default off) is on, when
dynamically updating this field, consider that
it may impact scalability by changing the amount of traffic the Kubelet
sends to the API server.
Default: 10
   -->
   <p><code>kubeAPIBurst</code>设置与 Kubernetes API 服务器通信时突发的流量级别。
此字段取值不可以是负数。</p>
   <p>当 <code>DynamicKubeletConfig</code> （已弃用，默认为关闭）被启用时，
如果动态更新了此字段，请考虑这可能因为 kubelet 与 API 服务器之间流量的变化而影响集群扩缩能力。</p>
   <p>默认值：10</p>
</td>
</tr>

<tr><td><code>serializeImagePulls</code><br/>
<code>bool</code>
</td>
<td>
   <!--serializeImagePulls when enabled, tells the Kubelet to pull images one
at a time. We recommend &lowast;not&lowast; changing the default value on nodes that
run docker daemon with version  < 1.9 or an Aufs storage backend.
Issue #10959 has more details.
If DynamicKubeletConfig (deprecated; default off) is on, when
dynamically updating this field, consider that
it may impact the performance of image pulls.
Default: true
   -->
   <p><code>serializeImagePulls</code>被启用时会通知 kubelet 每次仅拉取一个镜像。
我们建议<em>不要</em>在所运行的 docker 守护进程版本低于 1.9、使用 aufs
存储后端的节点上更改默认值。详细信息可参见 Issue #10959。</p>
   <p>当 <code>DynamicKubeletConfig</code> （已弃用，默认为关闭）被启用时，
如果动态更新了此字段，请考虑这可能会影响镜像拉取的性能。</p>
   <p>默认值：true</p>
</td>
</tr>

<tr><td><code>evictionHard</code><br/>
<code>map[string]string</code>
</td>
<td>
   <!--evictionHard is a map of signal names to quantities that defines hard eviction thresholds. 
For example: <code>{&quot;memory.available&quot;: &quot;300Mi&quot;}</code>.
To explicitly disable, pass a 0% or 100% threshold on an arbitrary resource.
If DynamicKubeletConfig (deprecated; default off) is on, when
dynamically updating this field, consider that
it may trigger or delay Pod evictions.
Default:
  memory.available:  "100Mi"
  nodefs.available:  "10%"
  nodefs.inodesFree: "5%"
  imagefs.available: "15%"
   -->
   <p><code>evictionHard</code>是一个映射，是从信号名称到定义硬性驱逐阈值的映射。
例如：<code>{&quot;memory.available&quot;: &quot;300Mi&quot;}</code>。
如果希望显式地禁用，可以在任意资源上将其阈值设置为 0% 或 100%。</p>
   <p>当 <code>DynamicKubeletConfig</code> （已弃用，默认为关闭）被启用时，
如果动态更新了此字段，请考虑这可能会触发或延迟 Pod 驱逐操作。</p>
   <p>默认值：</p>
   <code><pre>
  memory.available:  "100Mi"
  nodefs.available:  "10%"
  nodefs.inodesFree: "5%"
  imagefs.available: "15%"
  </pre></code>
</td>
</tr>

<tr><td><code>evictionSoft</code><br/>
<code>map[string]string</code>
</td>
<td>
   <!--evictionSoft is a map of signal names to quantities that defines soft eviction thresholds.
For example: <code>{&quot;memory.available&quot;: &quot;300Mi&quot;}</code>.
If DynamicKubeletConfig (deprecated; default off) is on, when
dynamically updating this field, consider that
it may trigger or delay Pod evictions, and may change the allocatable reported
by the node.
Default: nil
   -->
   <p><code>evictionSoft</code>是一个映射，是从信号名称到定义软性驱逐阈值的映射。
例如：<code>{&quot;memory.available&quot;: &quot;300Mi&quot;}</code>。</p>
   <p>当 <code>DynamicKubeletConfig</code> （已弃用，默认为关闭）被启用时，
如果动态更新了此字段，请考虑这可能会触发或延迟 Pod 驱逐操作，
并且可能造成节点所报告的可分配资源数量发生变化。</p>
   <p>默认值：nil</p>
</td>
</tr>

<tr><td><code>evictionSoftGracePeriod</code><br/>
<code>map[string]string</code>
</td>
<td>
   <!--evictionSoftGracePeriod is a map of signal names to quantities that defines grace
periods for each soft eviction signal. For example: <code>{&quot;memory.available&quot;: &quot;30s&quot;}</code>.
If DynamicKubeletConfig (deprecated; default off) is on, when
dynamically updating this field, consider that
it may trigger or delay Pod evictions.
Default: nil
   -->
   <p><code>evictionSoftGracePeriod</code>是一个映射，是从信号名称到每个软性驱逐信号的宽限期限。
例如：<code>{&quot;memory.available&quot;: &quot;30s&quot;}</code>。</p>
   <p>当 <code>DynamicKubeletConfig</code> （已弃用，默认为关闭）被启用时，
如果动态更新了此字段，请考虑这可能会触发或延迟 Pod 驱逐操作。</p>
   <p>默认值：nil</p>
</td>
</tr>

<tr><td><code>evictionPressureTransitionPeriod</code><br/>
<a href="https://godoc.org/k8s.io/apimachinery/pkg/apis/meta/v1#Duration"><code>meta/v1.Duration</code></a>
</td>
<td>
   <!--evictionPressureTransitionPeriod is the duration for which the kubelet has to wait
before transitioning out of an eviction pressure condition.
If DynamicKubeletConfig (deprecated; default off) is on, when
dynamically updating this field, consider that
lowering it may decrease the stability of the node when the node is overcommitted.
Default: &quot;5m&quot;
   -->
   <p><code>evictionPressureTransitionPeriod</code>设置 kubelet
离开驱逐压力状况之前必须要等待的时长。</p>
   <p>当 <code>DynamicKubeletConfig</code> （已弃用，默认为关闭）被启用时，
如果动态更新了此字段，请考虑减少此字段值可能会在节点过量分配时降低节点稳定性。</p>
   <p>默认值：&quot;5m&quot;</p>
</td>
</tr>

<tr><td><code>evictionMaxPodGracePeriod</code><br/>
<code>int32</code>
</td>
<td>
   <!--evictionMaxPodGracePeriod is the maximum allowed grace period (in seconds) to use
when terminating pods in response to a soft eviction threshold being met. This value
effectively caps the Pod's terminationGracePeriodSeconds value during soft evictions.
Note: Due to issue #64530, the behavior has a bug where this value currently just
overrides the grace period during soft eviction, which can increase the grace
period from what is set on the Pod. This bug will be fixed in a future release.
If DynamicKubeletConfig (deprecated; default off) is on, when
dynamically updating this field, consider that
lowering it decreases the amount of time Pods will have to gracefully clean
up before being killed during a soft eviction.
Default: 0
   -->
   <p><code>evictionMaxPodGracePeriod</code>是指达到软性逐出阈值而引起 Pod 终止时，
可以赋予的宽限期限最大值（按秒计）。这个值本质上限制了软性逐出事件发生时，
Pod 可以获得的<code>terminationGracePeriodSeconds</code>。</p>
   <p>注意：由于 Issue #64530 的原因，系统中存在一个缺陷，即此处所设置的值会在软性逐出时覆盖
Pod 的宽限期设置，从而有可能增加 Pod 上原本设置的宽限期限时长。
这个缺陷会在未来版本中修复。</p>
   <p>当 <code>DynamicKubeletConfig</code> （已弃用，默认为关闭）被启用时，
如果动态更新了此字段，请考虑缩短此宽限期限值会导致软性逐出期间 Pod
在被杀死之前用来体面地完成清理工作可用的时间。</p>
   <p>默认值：0</p>
</td>
</tr>

<tr><td><code>evictionMinimumReclaim</code><br/>
<code>map[string]string</code>
</td>
<td>
   <!--evictionMinimumReclaim is a map of signal names to quantities that defines minimum reclaims,
which describe the minimum amount of a given resource the kubelet will reclaim when
performing a pod eviction while that resource is under pressure.
For example: <code>{&quot;imagefs.available&quot;: &quot;2Gi&quot;}</code>.
If DynamicKubeletConfig (deprecated; default off) is on, when
dynamically updating this field, consider that
it may change how well eviction can manage resource pressure.
Default: nil
   -->
   <p><code>evictionMinimumReclaim</code>是一个映射，定义信号名称与最小回收量数值之间的关系。
最小回收量指的是资源压力较大而执行 Pod 驱逐操作时，kubelet 对给定资源的最小回收量。
例如：<code>{&quot;imagefs.available&quot;: &quot;2Gi&quot;}</code>。</p>
   <p>当 <code>DynamicKubeletConfig</code> （已弃用，默认为关闭）被启用时，
如果动态更新了此字段，请考虑这可能会改变驱逐操作应对资源压力的效果。</p>
   <p>默认值：nil</p>
</td>
</tr>

<tr><td><code>podsPerCore</code><br/>
<code>int32</code>
</td>
<td>
   <!--podsPerCore is the maximum number of pods per core. Cannot exceed maxPods.
The value must be a non-negative integer.
If 0, there is no limit on the number of Pods.
If DynamicKubeletConfig (deprecated; default off) is on, when
dynamically updating this field, consider that
changes may cause Pods to fail admission on Kubelet restart, and may change
the value reported in `Node.status.capacity.pods`, thus affecting
future scheduling decisions. Increasing this value may also decrease performance,
as more Pods can be packed into a single node.
Default: 0
   -->
   <p><code>podsPerCore</code>设置的是每个核上 Pod 个数上限。此值不能超过<code>maxPods</code>。
所设值必须是非负整数。如果设置为 0，则意味着对 Pod 个数没有限制。</p>
   <p>当 <code>DynamicKubeletConfig</code> （已弃用，默认为关闭）被启用时，
如果动态更新了此字段，请考虑变更可能导致 kubelet 重启时 Pod 无法被准入，
还可能导致<code>Node.status.capacity.pods</code>所报告的数值发生变化，
进而影响到将来的调度决策。增大此值也会降低性能，因为在同一个处理器核上需要运行更多的 Pod。</p>
   <p>默认值：0</p>
</td>
</tr>

<tr><td><code>enableControllerAttachDetach</code><br/>
<code>bool</code>
</td>
<td>
   <!--enableControllerAttachDetach enables the Attach/Detach controller to
manage attachment/detachment of volumes scheduled to this node, and
disables kubelet from executing any attach/detach operations.
If DynamicKubeletConfig (deprecated; default off) is on, when
dynamically updating this field, consider that
changing which component is responsible for volume management on a live node
may result in volumes refusing to detach if the node is not drained prior to
the update, and if Pods are scheduled to the node before the
volumes.kubernetes.io/controller-managed-attach-detach annotation is updated by the
Kubelet. In general, it is safest to leave this value set the same as local config.
Default: true
   -->
   <p><code>enableControllerAttachDetach</code>用来允许 Attach/Detach
控制器管理调度到本节点的卷的挂接（attachment）和解除挂接（detachement），
并且禁止 kubelet 执行任何 attach/detach 操作。</p>
   <p>当 <code>DynamicKubeletConfig</code> （已弃用，默认为关闭）被启用时，
如果动态更新了此字段，请考虑在运行中的节点上更改由哪个组件来负责卷管理时，
这一变更可能导致节点在被更新前尚未腾空时卷无法被解除挂接。
如果 kubelet 尚未更新<code>volumes.kubernetes.io/controller-managed-attach-detach</code>
注解时 Pod 已经被调度到了该节点，节点上的卷也会无法解除挂接。
一般而言，最安全的做法是将此字段设置为与本地配置相同的值。</p>
   <p>默认值：true</p>
</td>
</tr>

<tr><td><code>protectKernelDefaults</code><br/>
<code>bool</code>
</td>
<td>
   <!--protectKernelDefaults, if true, causes the Kubelet to error if kernel
flags are not as it expects. Otherwise the Kubelet will attempt to modify
kernel flags to match its expectation.
If DynamicKubeletConfig (deprecated; default off) is on, when
dynamically updating this field, consider that
enabling it may cause the Kubelet to crash-loop if the Kernel is not configured as
Kubelet expects.
Default: false
   -->
   <p><code>protectKernelDefaults</code>设置为<code>true</code>时，会令 kubelet
在发现内核参数与预期不符时出错退出。若此字段设置为<code>false</code>，则 kubelet
会尝试更改内核参数以满足其预期。</p>
   <p>当 <code>DynamicKubeletConfig</code> （已弃用，默认为关闭）被启用时，
如果动态更新了此字段，请考虑启用此设置会在内核参数与 kubelet 预期不匹配时导致
kubelet 进入崩溃循环（Crash-Loop）状态。</p>
   <p>默认值：false</p>
</td>
</tr>

<tr><td><code>makeIPTablesUtilChains</code><br/>
<code>bool</code>
</td>
<td>
   <!--makeIPTablesUtilChains, if true, causes the Kubelet ensures a set of iptables rules
are present on host.
These rules will serve as utility rules for various components, e.g. kube-proxy.
The rules will be created based on iptablesMasqueradeBit and iptablesDropBit.
If DynamicKubeletConfig (deprecated; default off) is on, when
dynamically updating this field, consider that
disabling it will prevent the Kubelet from healing locally misconfigured iptables rules.
Default: true
   -->
   <p><code>makeIPTablesUtilChains</code>设置为<code>true</code>时，相当于允许 kubelet
确保一组 iptables 规则存在于宿主机上。这些规则会为不同的组件（例如 kube-proxy）
提供工具性质的规则。它们是基于<code>iptablesMasqueradeBit</code>和<code>iptablesDropBit</code>
来创建的。</p>
   <p>当 <code>DynamicKubeletConfig</code> （已弃用，默认为关闭）被启用时，
如果动态更新了此字段，请考虑禁用此行为会导致 kubelet 无法在本地 iptables
规则出错时实现自愈。</p>
   <p>默认值：true</p>
</td>
</tr>

<tr><td><code>iptablesMasqueradeBit</code><br/>
<code>int32</code>
</td>
<td>
   <!--iptablesMasqueradeBit is the bit of the iptables fwmark space to mark for SNAT.
Values must be within the range [0, 31]. Must be different from other mark bits.
Warning: Please match the value of the corresponding parameter in kube-proxy.
TODO: clean up IPTablesMasqueradeBit in kube-proxy.
If DynamicKubeletConfig (deprecated; default off) is on, when
dynamically updating this field, consider that
it needs to be coordinated with other components, like kube-proxy, and the update
will only be effective if MakeIPTablesUtilChains is enabled.
Default: 14
   -->
   <p><code>iptablesMasqueradeBit</code>是 iptables fwmark 空间中用来为 SNAT
作标记的位。此值必须介于<code>[0, 31]</code>区间，必须与其他标记位不同。</p>
   <p>警告：请确保此值设置与 kube-proxy 中对应的参数设置取值相同。</p>
   <p>当 <code>DynamicKubeletConfig</code> （已弃用，默认为关闭）被启用时，
如果动态更新了此字段，请考虑此处的变更要与其他组件（如 kube-proxy）相应的变更协调一致。
只有当<code>makeIPTablesUtilChains</code>能力被启用时，这里的更新才会起作用。</p>
   <p>默认值：14</p>
</td>
</tr>

<tr><td><code>iptablesDropBit</code><br/>
<code>int32</code>
</td>
<td>
   <!--iptablesDropBit is the bit of the iptables fwmark space to mark for dropping packets.
Values must be within the range [0, 31]. Must be different from other mark bits.
If DynamicKubeletConfig (deprecated; default off) is on, when
dynamically updating this field, consider that
it needs to be coordinated with other components, like kube-proxy, and the update
will only be effective if MakeIPTablesUtilChains is enabled.
Default: 15
   -->
   <p><code>iptablesDropBit</code>是 iptables fwmark 空间中用来标记丢弃包的数据位。
此值必须介于<code>[0, 31]</code>区间，必须与其他标记位不同。</p>
   <p>当 <code>DynamicKubeletConfig</code> （已弃用，默认为关闭）被启用时，
如果动态更新了此字段，请考虑此处的变更要与其他组件（如 kube-proxy）相应的变更协调一致。
只有当<code>makeIPTablesUtilChains</code>能力被启用时，这里的更新才会起作用。</p>
   <p>默认值：15</p>
</td>
</tr>

<tr><td><code>featureGates</code><br/>
<code>map[string]bool</code>
</td>
<td>
   <!--featureGates is a map of feature names to bools that enable or disable experimental
features. This field modifies piecemeal the built-in default values from
"k8s.io/kubernetes/pkg/features/kube_features.go".
If DynamicKubeletConfig (deprecated; default off) is on, when
dynamically updating this field, consider the
documentation for the features you are enabling or disabling. While we
encourage feature developers to make it possible to dynamically enable
and disable features, some changes may require node reboots, and some
features may require careful coordination to retroactively disable.
Default: nil
   -->
   <p><code>featureGates</code>是一个从功能特性名称到布尔值的映射，用来启用或禁用实验性的功能。
此字段可逐条更改文件 &quot;k8s.io/kubernetes/pkg/features/kube_features.go&quot;
中所给的内置默认值。</p>
   <p>当 <code>DynamicKubeletConfig</code> （已弃用，默认为关闭）被启用时，
如果动态更新了此字段，请考虑你所启用或禁止的功能特性的文档。
尽管我们鼓励功能特性的开发人员使动态启用或禁用功能特性成为可能，
某些变更可能要求重新启动节点，某些特性可能要求在从启用到禁用切换时作出精细的协调。</p>
   <p>默认值：nil</p>
</td>
</tr>

<tr><td><code>failSwapOn</code><br/>
<code>bool</code>
</td>
<td>
   <!--failSwapOn tells the Kubelet to fail to start if swap is enabled on the node.
If DynamicKubeletConfig (deprecated; default off) is on, when
dynamically updating this field, consider that
setting it to true will cause the Kubelet to crash-loop if swap is enabled.
Default: true
   -->
   <p><code>failSwapOn</code>通知 kubelet 在节点上启用交换分区时拒绝启动。</p>
   <p>当 <code>DynamicKubeletConfig</code> （已弃用，默认为关闭）被启用时，
如果动态更新了此字段，请考虑缩短此周期长度可能产生性能影响。</p>
   <p>默认值：true</p>
</td>
</tr>

<tr><td><code>memorySwap</code><br/>
<a href="#kubelet-config-k8s-io-v1beta1-MemorySwapConfiguration"><code>MemorySwapConfiguration</code></a>
</td>
<td>
   <!--memorySwap configures swap memory available to container workloads.
   -->
   <p><code>memorySwap</code>配置容器负载可用的交换内存。</p>
</td>
</tr>

<tr><td><code>containerLogMaxSize</code><br/>
<code>string</code>
</td>
<td>
   <!--containerLogMaxSize is a quantity defining the maximum size of the container log
file before it is rotated. For example: &quot;5Mi&quot; or &quot;256Ki&quot;.
If DynamicKubeletConfig (deprecated; default off) is on, when
dynamically updating this field, consider that
it may trigger log rotation.
Default: &quot;10Mi&quot;
   -->
   <p><code>containerLogMaxSize</code>是定义容器日志文件被轮转之前可以到达的最大尺寸。
例如：&quot;5Mi&quot; 或 &quot;256Ki&quot;。</p>
   <p>当 <code>DynamicKubeletConfig</code> （已弃用，默认为关闭）被启用时，
如果动态更新了此字段，请考虑可能会触发日志轮转。</p>
   <p>默认值：&quot;10Mi&quot;</p>
</td>
</tr>

<tr><td><code>containerLogMaxFiles</code><br/>
<code>int32</code>
</td>
<td>
   <!--containerLogMaxFiles specifies the maximum number of container log files that can
be present for a container.
If DynamicKubeletConfig (deprecated; default off) is on, when
dynamically updating this field, consider that
lowering it may cause log files to be deleted.
Default: 5
   -->
   <p><code>containerLogMaxFiles</code>设置每个容器可以存在的日志文件个数上限。</p>
   <p>当 <code>DynamicKubeletConfig</code> （已弃用，默认为关闭）被启用时，
如果动态更新了此字段，请考虑降低此值可能导致日志文件被删除。</p>
   <p>默认值：&quot;5&quot;</p>
</td>
</tr>

<tr><td><code>configMapAndSecretChangeDetectionStrategy</code><br/>
<a href="#kubelet-config-k8s-io-v1beta1-ResourceChangeDetectionStrategy"><code>ResourceChangeDetectionStrategy</code></a>
</td>
<td>
   <!--
   <p>configMapAndSecretChangeDetectionStrategy is a mode in which ConfigMap and Secret
managers are running. Valid values include:</p>
<ul>
<li><code>Get</code>: kubelet fetches necessary objects directly from the API server;</li>
<li><code>Cache</code>: kubelet uses TTL cache for object fetched from the API server;</li>
<li><code>Watch</code>: kubelet uses watches to observe changes to objects that are in its interest.</li>
</ul>
<p>Default: &quot;Watch&quot;</p>
   -->
   <p><code>configMapAndSecretChangeDetectionStrategy</code>是 ConfigMap 和 Secret
管理器的运行模式。合法值包括：</p>
   <ul>
    <li><code>Get</code>：kubelet 从 API 服务器直接取回必要的对象；</li>
    <li><code>Cache</code>：kubelet 使用 TTL 缓存来管理来自 API 服务器的对象；</li>
    <li><code>Watch</code>：kubelet 使用 watch 操作来观察所关心的对象的变更。</li>
    </ul>
   <p>默认值：&quot;Watch&quot;</p>
</td>
</tr>

<tr><td><code>systemReserved</code><br/>
<code>map[string]string</code>
</td>
<td>
   <!--systemReserved is a set of ResourceName=ResourceQuantity (e.g. cpu=200m,memory=150G)
pairs that describe resources reserved for non-kubernetes components.
Currently only cpu and memory are supported.
See http://kubernetes.io/docs/user-guide/compute-resources for more detail.
If DynamicKubeletConfig (deprecated; default off) is on, when
dynamically updating this field, consider that
it may not be possible to increase the reserved resources, because this
requires resizing cgroups. Always look for a NodeAllocatableEnforced event
after updating this field to ensure that the update was successful.
Default: nil
   -->
   <p><code>systemReserved</code>是一组<code>资源名称=资源数量</code>对，
用来描述为非 Kubernetes 组件预留的资源（例如：'cpu=200m,memory=150G'）。</p>
   <p>目前仅支持 CPU 和内存。更多细节可参见 http://kubernetes.io/zh/docs/user-guide/compute-resources。</p>
   <p>当 <code>DynamicKubeletConfig</code> （已弃用，默认为关闭）被启用时，
如果动态更新了此字段，请考虑增加预留资源也许是不可能的，因为需要改变控制组大小。
在更改了此字段之后，应该总是关注<code>NodeAllocatableEnforced</code>事件，
以确保更新是成功的。</p>
   <p>默认值：Nil</p>
</td>
</tr>

<tr><td><code>kubeReserved</code><br/>
<code>map[string]string</code>
</td>
<td>
   <!--kubeReserved is a set of ResourceName=ResourceQuantity (e.g. cpu=200m,memory=150G) pairs
that describe resources reserved for kubernetes system components.
Currently cpu, memory and local storage for root file system are supported.
See https://kubernetes.io/docs/concepts/configuration/manage-resources-containers/
for more details.
If DynamicKubeletConfig (deprecated; default off) is on, when
dynamically updating this field, consider that
it may not be possible to increase the reserved resources, because this
requires resizing cgroups. Always look for a NodeAllocatableEnforced event
after updating this field to ensure that the update was successful.
Default: nil
   -->
   <p><code>kubeReserved</code>是一组<code>资源名称=资源数量</code>对，
用来描述为 Kubernetes 系统组件预留的资源（例如：'cpu=200m,memory=150G'）。
目前支持 CPU、内存和根文件系统的本地存储。
更多细节可参见 https://kubernetes.io/zh/docs/concepts/configuration/manage-resources-containers/。</p>
   <p>当 <code>DynamicKubeletConfig</code> （已弃用，默认为关闭）被启用时，
如果动态更新了此字段，请考虑增加预留资源也许是不可能的，因为需要改变控制组大小。
在更改了此字段之后，应该总是关注<code>NodeAllocatableEnforced</code>事件，
以确保更新是成功的。</p>
   <p>默认值：Nil</p>
</td>
</tr>

<tr><td><code>reservedSystemCPUs</code> <B>[必需]</B><br/>
<code>string</code>
</td>
<td>
   <!--The reservedSystemCPUs option specifies the CPU list reserved for the host
level system threads and kubernetes related threads. This provide a &quot;static&quot;
CPU list rather than the &quot;dynamic&quot; list by systemReserved and kubeReserved.
This option does not support systemReservedCgroup or kubeReservedCgroup.
   -->
   <p><code>reservedSystemCPUs</code>选项设置为宿主级系统线程和 Kubernetes
相关线程所预留的 CPU 列表。此字段提供的是一种“静态”的 CPU 列表，而不是像
<code>systemReserved</code>和<code>kubeReserved</code>所提供的“动态”列表。
此选项不支持<code>systemReservedCgroup</code>或<code>kubeReservedCgroup</code>。</p>
</td>
</tr>

<tr><td><code>showHiddenMetricsForVersion</code><br/>
<code>string</code>
</td>
<td>
   <!--showHiddenMetricsForVersion is the previous version for which you want to show
hidden metrics.
Only the previous minor version is meaningful, other values will not be allowed.
The format is <code>&lt;major&gt;.&lt;minor&gt;</code>, e.g.: <code>1.16</code>.
The purpose of this format is make sure you have the opportunity to notice
if the next release hides additional metrics, rather than being surprised
when they are permanently removed in the release after that.
Default: &quot;&quot;
   -->
   <p><code>showHiddenMetricsForVersion<code>是你希望显示隐藏度量值的上一版本。
只有上一个次版本是有意义的，其他值都是不允许的。
字段值的格式为<code>&lt;major&gt;.&lt;minor&gt;</code>，例如：<code>1.16</code>。
此格式的目的是为了确保在下一个版本中有新的度量值被隐藏时，你有机会注意到这类变化，
而不是当这些度量值在其后的版本中彻底去除时来不及应对。</p>
   <p>默认值：&quot;&quot;</p>
</td>
</tr>

<tr><td><code>systemReservedCgroup</code><br/>
<code>string</code>
</td>
<td>
   <!--systemReservedCgroup helps the kubelet identify absolute name of top level CGroup used
to enforce <code>systemReserved</code> compute resource reservation for OS system daemons.
Refer to [Node Allocatable](https://git.k8s.io/community/contributors/design-proposals/node/node-allocatable.md)
doc for more information.
Dynamic Kubelet Config (deprecated): This field should not be updated without a full node
reboot. It is safest to keep this value the same as the local config.
Default: &quot;&quot;
   -->
   <p><code>systemReservedCgroup</code>帮助 kubelet 识别用来为 OS 系统级守护进程实施
<code>systemReserved</code>计算资源预留时使用的顶级控制组（CGroup）。
参考[Node Allocatable](https://git.k8s.io/community/contributors/design-proposals/node/node-allocatable.md)
以了解详细信息。</p>
   <p><code>DynamicKubeletConfig</code>（已弃用）：
此字段更新时需要整个节点重启。最安全的做法是保持此值与本地配置相同。</p>
   <p>默认值：&quot;&quot;</p>
</td>
</tr>


<tr><td><code>kubeReservedCgroup</code><br/>
<code>string</code>
</td>
<td>
   <!--kubeReservedCgroup helps the kubelet identify absolute name of top level CGroup used
to enforce `KubeReserved` compute resource reservation for Kubernetes node system daemons.
Refer to [Node Allocatable](https://git.k8s.io/community/contributors/design-proposals/node/node-allocatable.md)
doc for more information.
Dynamic Kubelet Config (deprecated): This field should not be updated without a full node
reboot. It is safest to keep this value the same as the local config.
Default: ""
   -->
   <p><code>kubeReservedCgroup</code> 帮助 kubelet 识别用来为 Kubernetes 节点系统级守护进程实施
<code>kubeReserved</code>计算资源预留时使用的顶级控制组（CGroup）。
参阅<a href="https://git.k8s.io/community/contributors/design-proposals/node/node-allocatable.md">Node Allocatable</a>
了解进一步的信息。</p>
   <p><code>DynamicKubeletConfig</code>（已弃用）：
此字段更新时需要整个节点重启。最安全的做法是保持此值与本地配置相同。</p>
   <p>默认值：&quot;&quot;</p>
</td>
</tr>

<tr><td><code>enforceNodeAllocatable</code><br/>
<code>[]string</code>
</td>
<td>
   <!--This flag specifies the various Node Allocatable enforcements that Kubelet needs to perform.
This flag accepts a list of options. Acceptable options are <code>none</code>, <code>pods</code>,
<code>system-reserved</code> and <code>kube-reserved</code>.
If <code>none</code> is specified, no other options may be specified.
When <code>system-reserved</code> is in the list, systemReservedCgroup must be specified.
When <code>kube-reserved</code> is in the list, kubeReservedCgroup must be specified.
This field is supported only when <code>cgroupsPerQOS</code> is set to true.
Refer to <a href="https://git.k8s.io/community/contributors/design-proposals/node/node-allocatable.md">Node Allocatable</a>
for more information.
If DynamicKubeletConfig (deprecated; default off) is on, when
dynamically updating this field, consider that
removing enforcements may reduce the stability of the node. Alternatively, adding
enforcements may reduce the stability of components which were using more than
the reserved amount of resources; for example, enforcing kube-reserved may cause
Kubelets to OOM if it uses more than the reserved resources, and enforcing system-reserved
may cause system daemons to OOM if they use more than the reserved resources.
Default: [&quot;pods&quot;]
   -->
   <p>此标志设置 kubelet 需要执行的各类节点可分配资源策略。此字段接受一组选项列表。
可接受的选项有<code>none</code>、<code>pods</code>、<code>system-reserved</code>和
<code>kube-reserved</code>。</p>
   <p>如果设置了<code>none</code>，则字段值中不可以包含其他选项。</p>
   <p>如果列表中包含<code>system-reserved</code>，则必须设置<code>systemReservedCgroup</code>。</p>
   <p>如果列表中包含<code>kube-reserved</code>，则必须设置<code>kubeReservedCgroup</code>。</p>
   <p>这个字段只有在<code>cgroupsPerQOS</code>被设置为<code>true</code>才被支持。</p>
   <p>参阅<a href="https://git.k8s.io/community/contributors/design-proposals/node/node-allocatable.md">Node Allocatable</a>
了解进一步的信息。</p>
   <p>当 <code>DynamicKubeletConfig</code> （已弃用，默认为关闭）被启用时，
如果动态更新了此字段，请考虑去掉此机制可能会降低节点稳定性。
反之，添加此机制可能会降低原来使用资源超出预留量的组件的稳定性。
例如，实施 kube-reserved 在 kubelet 使用资源超出预留量时可能导致 kubelet 发生 OOM，
而实施 system-reserved 机制可能导致使用资源超出预留量的系统守护进程发生 OOM。</p>
   <p>默认值：[&quot;pods&quot;]</p>
</td>
</tr>

<tr><td><code>allowedUnsafeSysctls</code><br/>
<code>[]string</code>
</td>
<td>
   <!--A comma separated whitelist of unsafe sysctls or sysctl patterns (ending in <code>*</code>).
Unsafe sysctl groups are <code>kernel.shm*</code>, <code>kernel.msg*</code>, <code>kernel.sem</code>, <code>fs.mqueue.*</code>,
and <code>net.*</code>. For example: &quot;<code>kernel.msg*,net.ipv4.route.min_pmtu</code>&quot;
Default: []
  -->
   <p>用逗号分隔的白名单列表，其中包含不安全的 sysctl 或 sysctl 模式（以<code>&lowast;</code>结尾）。
</p>
   <p>不安全的 sysctl 组有 <code>kernel.shm&lowast;</code>、<code>kernel.msg&lowast;</code>、
<code>kernel.sem</code>、<code>fs.mqueue.&lowast;</code> 和<code>net.&lowast;</code>。</p>
   <p>例如：&quot;<code>kernel.msg&lowast;,net.ipv4.route.min\_pmtu</code>&quot;</p>
   <p>默认值：[]</p>
</td>
</tr>

<tr><td><code>volumePluginDir</code><br/>
<code>string</code>
</td>
<td>
   <!--volumePluginDir is the full path of the directory in which to search
for additional third party volume plugins.
If DynamicKubeletConfig (deprecated; default off) is on, when
dynamically updating this field, consider that changing
the volumePluginDir may disrupt workloads relying on third party volume plugins.
Default: &quot;/usr/libexec/kubernetes/kubelet-plugins/volume/exec/&quot;
   -->
   <p><code>volumePluginDir</code>是用来搜索其他第三方卷插件的目录的路径。</p>
   <p>当 <code>DynamicKubeletConfig</code> （已弃用，默认为关闭）被启用时，
如果动态更新了此字段，请考虑更改<code>volumePluginDir</code>可能干扰使用第三方卷插件的负载。</p>
   <p>默认值：&quot;/usr/libexec/kubernetes/kubelet-plugins/volume/exec/&quot;</p>
</td>
</tr>

<tr><td><code>providerID</code><br/>
<code>string</code>
</td>
<td>
   <!--providerID, if set, sets the unique ID of the instance that an external
provider (i.e. cloudprovider) can use to identify a specific node.
If DynamicKubeletConfig (deprecated; default off) is on, when
dynamically updating this field, consider that
it may impact the ability of the Kubelet to interact with cloud providers.
Default: &quot;quot;
   -->
   <p><code>providerID</code>字段被设置时，指定的是一个外部提供者（即云驱动）实例的唯一 ID，
该提供者可用来唯一性地标识特定节点。</p>
   <p>当 <code>DynamicKubeletConfig</code> （已弃用，默认为关闭）被启用时，
如果动态更新了此字段，请考虑可能影响到 kubelet 与云驱动之间进行交互的能力。</p>
   <p>默认值：&quot;&quot;</p>
</td>
</tr>

<tr><td><code>kernelMemcgNotification</code><br/>
<code>bool</code>
</td>
<td>
   <!--kernelMemcgNotification, if set, instructs the the kubelet to integrate with the
kernel memcg notification for determining if memory eviction thresholds are
exceeded rather than polling.
If DynamicKubeletConfig (deprecated; default off) is on, when
dynamically updating this field, consider that
it may impact the way Kubelet interacts with the kernel.
Default: false
   -->
   <p><code>kernelMemcgNotification</code>字段如果被设置了，会告知 kubelet 集成内核的
memcg 通知机制来确定是否超出内存逐出阈值，而不是使用轮询机制来判定。</p>
   <p>当 <code>DynamicKubeletConfig</code> （已弃用，默认为关闭）被启用时，
如果动态更新了此字段，请考虑这样做可能影响到 kubelet 与内核的交互方式。</p>
   <p>默认值：false</p>
</td>
</tr>

<tr><td><code>logging</code> <B>[必需]</B><br/>
<a href="#LoggingConfiguration"><code>LoggingConfiguration</code></a>
</td>
<td>
   <!--logging specifies the options of logging.
Refer to <a href="https://github.com/kubernetes/component-base/blob/master/logs/options.go">Logs Options</a>
for more information.
Default:
  Format: text
   -->
   <p><code>logging</code>设置日志机制选项。更多的详细信息科参阅
<a href="https://github.com/kubernetes/component-base/blob/master/logs/options.go">日志选项</a>。</p>
   <p>默认值：</p>
   <code><pre>Format: text</pre></code>
</td>
</tr>

<tr><td><code>enableSystemLogHandler</code><br/>
<code>bool</code>
</td>
<td>
   <!--enableSystemLogHandler enables system logs via web interface host:port/logs/
Default: true
   -->
   <p><code>enableSystemLogHandler</code>用来启用通过 Web 接口 host:port/logs/
访问系统日志的能力。</p>
   <p>默认值：true</p>
</td>
</tr>

<tr><td><code>shutdownGracePeriod</code><br/>
<a href="https://godoc.org/k8s.io/apimachinery/pkg/apis/meta/v1#Duration"><code>meta/v1.Duration</code></a>
</td>
<td>
   <!--shutdownGracePeriod specifies the total duration that the node should delay the
shutdown and total grace period for pod termination during a node shutdown.
Default: &quot;0s&quot;
   -->
   <p><code>shutdownGracePeriod</code>设置节点关闭期间，节点自身需要延迟以及为
Pod 提供的宽限期限的总时长。</p>
   <p>默认值：&quot;0s&quot;</p>
</td>
</tr>

<tr><td><code>shutdownGracePeriodCriticalPods</code><br/>
<a href="https://godoc.org/k8s.io/apimachinery/pkg/apis/meta/v1#Duration"><code>meta/v1.Duration</code></a>
</td>
<td>
   <!--shutdownGracePeriodCriticalPods specifies the duration used to terminate critical
pods during a node shutdown. This should be less than shutdownGracePeriod.
For example, if shutdownGracePeriod=30s, and shutdownGracePeriodCriticalPods=10s,
during a node shutdown the first 20 seconds would be reserved for gracefully
terminating normal pods, and the last 10 seconds would be reserved for terminating
critical pods.
Default: &quot;0s&quot;
   -->
   <p><code>shutdownGracePeriodCriticalPods</code>设置节点关闭期间用来终止关键性
Pod 的时长。此时长要短于<code>shutdownGracePeriod</code>。
例如，如果<code>shutdownGracePeriod=30s</code>，<code>shutdownGracePeriodCriticalPods=10s<code>，
在节点关闭期间，前 20 秒钟被预留用来体面终止普通 Pod，后 10 秒钟用来终止关键 Pod。</p>
   <p>默认值：&quot;0s&quot;</p>
</td>
</tr>

<tr><td><code>shutdownGracePeriodByPodPriority</code><br/>
<a href="#kubelet-config-k8s-io-v1beta1-ShutdownGracePeriodByPodPriority"><code>[]ShutdownGracePeriodByPodPriority</code></a>
</td>
<td>
   <!--shutdownGracePeriodByPodPriority specifies the shutdown grace period for Pods based
on their associated priority class value.
When a shutdown request is received, the Kubelet will initiate shutdown on all pods
running on the node with a grace period that depends on the priority of the pod,
and then wait for all pods to exit.
Each entry in the array represents the graceful shutdown time a pod with a priority
class value that lies in the range of that value and the next higher entry in the
list when the node is shutting down.-->
   <p><code>shutdownGracePeriodByPodPriority</code>设置基于 Pod
相关的优先级类值而确定的体面关闭时间。当 kubelet 收到关闭请求的时候，kubelet
会针对节点上运行的所有 Pod 发起关闭操作，这些关闭操作会根据 Pod 的优先级确定其宽限期限，
之后 kubelet 等待所有 Pod 退出。</p>
   <p>数组中的每个表项代表的是节点关闭时 Pod 的体面终止时间；这里的 Pod
的优先级类介于列表中当前优先级类值和下一个表项的优先级类值之间。</p>
   <p>例如，要赋予关键 Pod 10 秒钟时间来关闭，赋予优先级&gt;=10000 Pod 20 秒钟时间来关闭，
赋予其余的 Pod 30 秒钟来关闭。</p>
   <p>shutdownGracePeriodByPodPriority:</p>
   <ul>
   <li>priority: 2000000000
   shutdownGracePeriodSeconds: 10</li>
   <li>priority: 10000
   shutdownGracePeriodSeconds: 20</li>
   <li>priority: 0
   shutdownGracePeriodSeconds: 30</li>
   </ul>
   <p>在退出之前，kubelet 要等待的时间上限为节点上所有优先级类的
<code>shutdownGracePeriodSeconds</code>的最大值。
当所有 Pod 都退出或者到达其宽限期限时，kubelet 会释放关闭防护锁。
此功能要求<code>GracefulNodeShutdown</code>特性门控被启用。</p>
   <p>当<code>shutdownGracePeriod</code>或<code>shutdownGracePeriodCriticalPods</code>
被设置时，此配置字段必须为空。</p>
   <p>默认值：nil</p>
</td>
</tr>

<tr><td><code>reservedMemory</code><br/>
<a href="#kubelet-config-k8s-io-v1beta1-MemoryReservation"><code>[]MemoryReservation</code></a>
</td>
<td>
   <!--reservedMemory specifies a comma-separated list of memory reservations for NUMA nodes.
The parameter makes sense only in the context of the memory manager feature.
The memory manager will not allocate reserved memory for container workloads.
For example, if you have a NUMA0 with 10Gi of memory and the reservedMemory was
specified to reserve 1Gi of memory at NUMA0, the memory manager will assume that
only 9Gi is available for allocation.
You can specify a different amount of NUMA node and memory types.
You can omit this parameter at all, but you should be aware that the amount of
reserved memory from all NUMA nodes should be equal to the amount of memory specified
by the <a href="https://kubernetes.io/docs/tasks/administer-cluster/reserve-compute-resources/#node-allocatable">node allocatable</a>.
If at least one node allocatable parameter has a non-zero value, you will need
to specify at least one NUMA node.
Also, avoid specifying:</p>
<ol>
<li>Duplicates, the same NUMA node, and memory type, but with a different value.</li>
<li>zero limits for any memory type.</li>
<li>NUMAs nodes IDs that do not exist under the machine.</li>
<li>memory types except for memory and hugepages-&lt;size&gt;</li>
</ol>
<p>Default: nil</p>
-->
   <p><code>reservedMemory</code>给出一个逗号分隔的列表，为 NUMA 节点预留内存。</p>
   <p>此参数仅在内存管理器功能特性语境下有意义。内存管理器不会为容器负载分配预留内存。
例如，如果你的 NUMA0 节点内存为 10Gi，<code>reservedMemory</code>设置为在 NUMA0
上预留 1Gi 内存，内存管理器会认为其上只有 9Gi 内存可供分配。</p>
   <p>你可以设置不同数量的 NUMA 节点和内存类型。你也可以完全忽略这个字段，不过你要清楚，
所有 NUMA 节点上预留内存的总量要等于通过
<a href="https://kubernetes.io/docs/tasks/administer-cluster/reserve-compute-resources/#node-allocatable">node allocatable</a>
设置的内存量。</p>
   <p>如果至少有一个节点可分配参数设置值非零，则你需要设置至少一个 NUMA 节点。</p>
   <p>此外，避免如下设置：</p>
   <ol>
   <li>在配置值中存在重复项，NUMA 节点和内存类型相同，但配置值不同，这是不允许的。</li>
   <li>为任何内存类型设置限制值为零。</li>
   <li>NUMA 节点 ID 在宿主系统上不存在。/li>
   <li>除<code>memory</code>和<code>hugepages-&lt;size&gt;</code>之外的内存类型。</li>
   </ol>
   <p>默认值：nil</p>
</td>
</tr>

<tr><td><code>enableProfilingHandler</code><br/>
<code>bool</code>
</td>
<td>
   <!--enableProfilingHandler enables profiling via web interface host:port/debug/pprof/
Default: true
   -->
   <p><code>enableProfilingHandler</code>启用通过 host:port/debug/pprof/ 接口来执行性能分析。</p>
   <p>默认值：true</p>
</td>
</tr>

<tr><td><code>enableDebugFlagsHandler</code><br/>
<code>bool</code>
</td>
<td>
   <!--enableDebugFlagsHandler enables flags endpoint via web interface host:port/debug/flags/v
Default: true
   -->
   <p><code>enableDebugFlagsHandler</code>启用通过 host:port/debug/flags/v Web
接口上的标志设置。</p>
   <p>默认值：true</p>
</td>
</tr>

<tr><td><code>seccompDefault</code><br/>
<code>bool</code>
</td>
<td>
   <!--SeccompDefault enables the use of <code>RuntimeDefault</code> as the default seccomp profile for all workloads.
This requires the corresponding SeccompDefault feature gate to be enabled as well.
Default: false
   -->
   <p><code>seccompDefault</code>字段允许针对所有负载将<code>RuntimeDefault</code>
设置为默认的 seccomp 配置。这一设置要求对应的<code>SeccompDefault</code>特性门控被启用。</p>
   <p>默认值：false</p>
</td>
</tr>

<tr><td><code>memoryThrottlingFactor</code><br/>
<code>float64</code>
</td>
<td>
   <!--MemoryThrottlingFactor specifies the factor multiplied by the memory limit or node allocatable memory
when setting the cgroupv2 memory.high value to enforce MemoryQoS.
Decreasing this factor will set lower high limit for container cgroups and put heavier reclaim pressure
while increasing will put less reclaim pressure.
See http://kep.k8s.io/2570 for more details.
Default: 0.8
   -->
   <p>当设置 cgroupv2 <code>memory.high</code>以实施<code>MemoryQoS</code>特性时，
<code>memoryThrottlingFactor</code>用来作为内存限制或节点可分配内存的系数。</p>
   <p>减小此系数会为容器控制组设置较低的 high 限制值，从而增大回收压力；反之，
增大此系数会降低回收压力。更多细节参见 http://kep.k8s.io/2570。</p>
   <p>默认值：0.8</p>
</td>
</tr>

<tr><td><code>registerWithTaints</code><br/>
<a href="https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.23/#taint-v1-core"><code>[]core/v1.Taint</code></a>
</td>
<td>
   <!--registerWithTaints are an array of taints to add to a node object when
the kubelet registers itself. This only takes effect when registerNode
is true and upon the initial registration of the node.
Default: nil
   -->
   <p><code>registerWithTaints</code>是一个由污点组成的数组，包含 kubelet
注册自身时要向节点对象添加的污点。只有<code>registerNode</code>为<code>true</code>
时才会起作用，并且仅在节点的最初注册时起作用。</p>
   <p>默认值：nil</p>
</td>
</tr>

<tr><td><code>registerNode</code><br/>
<code>bool</code>
</td>
<td>
   <!--registerNode enables automatic registration with the apiserver.
Default: true
   -->
   <p><code>registerNode</code>启用向 API 服务器的自动注册。</p>
   <p>默认值：true</p>
</td>
</tr>
</tbody>
</table>

## `SerializedNodeConfigSource`     {#kubelet-config-k8s-io-v1beta1-SerializedNodeConfigSource}

<!--
SerializedNodeConfigSource allows us to serialize v1.NodeConfigSource.
This type is used internally by the Kubelet for tracking checkpointed dynamic configs.
It exists in the kubeletconfig API group because it is classified as a versioned input to the Kubelet.
-->
SerializedNodeConfigSource 允许对 `v1.NodeConfigSource` 执行序列化操作。
这一类型供 kubelet 内部使用，以便跟踪动态配置的检查点。
此资源存在于 kubeletconfig API 组是因为它被当做是对 kubelet 的一种版本化输入。

<table class="table">
<thead><tr><th width="30%"><!--Field-->字段</th><th><!--Description-->描述</th></tr></thead>
<tbody>

<tr><td><code>apiVersion</code><br/>string</td><td><code>kubelet.config.k8s.io/v1beta1</code></td></tr>
<tr><td><code>kind</code><br/>string</td><td><code>SerializedNodeConfigSource</code></td></tr>

<tr><td><code>source</code><br/>
<a href="https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.23/#nodeconfigsource-v1-core"><code>core/v1.NodeConfigSource</code></a>
</td>
<td>
   <!--source is the source that we are serializing.
   -->
   <p><code>source</code>是我们执行序列化的数据源。</p>
</td>
</tr>

</tbody>
</table>

## `KubeletAnonymousAuthentication`     {#kubelet-config-k8s-io-v1beta1-KubeletAnonymousAuthentication}

<!--
**Appears in:**
-->
**出现在：**

- [KubeletAuthentication](#kubelet-config-k8s-io-v1beta1-KubeletAuthentication)

<table class="table">
<thead><tr><th width="30%"><!--Field-->字段</th><th><!--Description-->描述</th></tr></thead>
<tbody>

<tr><td><code>enabled</code><br/>
<code>bool</code>
</td>
<td>
   <!--
   <p>enabled allows anonymous requests to the kubelet server.
Requests that are not rejected by another authentication method are treated as
anonymous requests.
Anonymous requests have a username of <code>system:anonymous</code>, and a group name of
<code>system:unauthenticated</code>.</p>
   -->
   <p><code>enabled</code>允许匿名用户向 kubelet 服务器发送请求。
未被其他身份认证方法拒绝的请求都会被当做匿名请求。
匿名请求对应的用户名为<code>system:anonymous</code>，对应的用户组名为
<code>system:unauthenticated</code>。</p>
</td>
</tr>
</tbody>
</table>

## `KubeletAuthentication`     {#kubelet-config-k8s-io-v1beta1-KubeletAuthentication}

<!--
**Appears in:**
-->
**出现在：**

- [KubeletConfiguration](#kubelet-config-k8s-io-v1beta1-KubeletConfiguration)

<table class="table">
<thead><tr><th width="30%"><!--Field-->字段</th><th><!--Description-->描述</th></tr></thead>
<tbody>

<tr><td><code>x509</code><br/>
<a href="#kubelet-config-k8s-io-v1beta1-KubeletX509Authentication"><code>KubeletX509Authentication</code></a>
</td>
<td>
   <!--x509 contains settings related to x509 client certificate authentication.
   -->
   <p><code>x509</code>包含与 x509 客户端证书认证相关的配置。</p>
</td>
</tr>

<tr><td><code>webhook</code><br/>
<a href="#kubelet-config-k8s-io-v1beta1-KubeletWebhookAuthentication"><code>KubeletWebhookAuthentication</code></a>
</td>
<td>
   <!--webhook contains settings related to webhook bearer token authentication.-->
   <p><code>webhook</code>包含与 Webhook 持有者令牌认证相关的配置。</p>
</td>
</tr>

<tr><td><code>anonymous</code><br/>
<a href="#kubelet-config-k8s-io-v1beta1-KubeletAnonymousAuthentication"><code>KubeletAnonymousAuthentication</code></a>
</td>
<td>
   <!--anonymous contains settings related to anonymous authentication.-->
   <p><code>anonymous</code>包含与匿名身份认证相关的配置信息。</p>
</td>
</tr>
</tbody>
</table>

## `KubeletAuthorization`     {#kubelet-config-k8s-io-v1beta1-KubeletAuthorization}

<!--
**Appears in:**
-->
**出现在：**

- [KubeletConfiguration](#kubelet-config-k8s-io-v1beta1-KubeletConfiguration)

<table class="table">
<thead><tr><th width="30%"><!--Field-->字段</th><th><!--Description-->描述</th></tr></thead>
<tbody>

<tr><td><code>mode</code><br/>
<a href="#kubelet-config-k8s-io-v1beta1-KubeletAuthorizationMode"><code>KubeletAuthorizationMode</code></a>
</td>
<td>
   <!--mode is the authorization mode to apply to requests to the kubelet server.
Valid values are <code>AlwaysAllow</code> and <code>Webhook</code>.
Webhook mode uses the SubjectAccessReview API to determine authorization.</p>
   -->
   <p><code>mode>是应用到 kubelet 服务器所接收到的请求上的鉴权模式。合法值包括
<code>AlwaysAllow</code>和<code>Webhook</code>。
Webhook 模式使用 <code>SubjectAccessReview</code> API 来确定鉴权。</p>
</td>
</tr>

<tr><td><code>webhook</code><br/>
<a href="#kubelet-config-k8s-io-v1beta1-KubeletWebhookAuthorization"><code>KubeletWebhookAuthorization</code></a>
</td>
<td>
   <!--webhook contains settings related to Webhook authorization.-->
   <p><code>webhook</code>包含与 Webhook 鉴权相关的配置信息。</p>
</td>
</tr>
</tbody>
</table>

## `KubeletAuthorizationMode`     {#kubelet-config-k8s-io-v1beta1-KubeletAuthorizationMode}

<!--
(Alias of `string`)
-->
（`string` 类型的别名）

<!--
**Appears in:**
-->
**出现在：**

- [KubeletAuthorization](#kubelet-config-k8s-io-v1beta1-KubeletAuthorization)

## `KubeletWebhookAuthentication`     {#kubelet-config-k8s-io-v1beta1-KubeletWebhookAuthentication}

<!--
**Appears in:**
-->
**出现在：**

- [KubeletAuthentication](#kubelet-config-k8s-io-v1beta1-KubeletAuthentication)

<table class="table">
<thead><tr><th width="30%"><!--Field-->字段</th><th><!--Description-->描述</th></tr></thead>
<tbody>

<tr><td><code>enabled</code><br/>
<code>bool</code>
</td>
<td>
   <!--enabled allows bearer token authentication backed by the
tokenreviews.authentication.k8s.io API.-->
   <p><code>enabled</code>允许使用<code>tokenreviews.authentication.k8s.io</code>
API 来提供持有者令牌身份认证。</p>
</td>
</tr>

<tr><td><code>cacheTTL</code><br/>
<a href="https://godoc.org/k8s.io/apimachinery/pkg/apis/meta/v1#Duration"><code>meta/v1.Duration</code></a>
</td>
<td>
   <!--cacheTTL enables caching of authentication results-->
   <p><code>cacheTTL</code>启用对身份认证结果的缓存。</p>
</td>
</tr>
</tbody>
</table>

## `KubeletWebhookAuthorization`     {#kubelet-config-k8s-io-v1beta1-KubeletWebhookAuthorization}

<!--
**Appears in:**
-->
**出现在：**

- [KubeletAuthorization](#kubelet-config-k8s-io-v1beta1-KubeletAuthorization)

<table class="table">
<thead><tr><th width="30%"><!--Field-->字段</th><th><!--Description-->描述</th></tr></thead>
<tbody>

<tr><td><code>cacheAuthorizedTTL</code><br/>
<a href="https://godoc.org/k8s.io/apimachinery/pkg/apis/meta/v1#Duration"><code>meta/v1.Duration</code></a>
</td>
<td>
   <!--cacheAuthorizedTTL is the duration to cache 'authorized' responses from the
webhook authorizer.-->
   <p><code>cacheAuthorizedTTL</code>设置来自 Webhook 鉴权组件的 'authorized'
响应的缓存时长。</p>
</td>
</tr>
<tr><td><code>cacheUnauthorizedTTL</code><br/>
<a href="https://godoc.org/k8s.io/apimachinery/pkg/apis/meta/v1#Duration"><code>meta/v1.Duration</code></a>
</td>
<td>
   <!--cacheUnauthorizedTTL is the duration to cache 'unauthorized' responses from
the webhook authorizer.-->
   <p><code>cacheUnauthorizedTTL</code>设置来自 Webhook 鉴权组件的 'unauthorized'
响应的缓存时长。</p>
</td>
</tr>
</tbody>
</table>

## `KubeletX509Authentication`     {#kubelet-config-k8s-io-v1beta1-KubeletX509Authentication}

<!--
**Appears in:**
-->
**出现在：**

- [KubeletAuthentication](#kubelet-config-k8s-io-v1beta1-KubeletAuthentication)

<table class="table">
<thead><tr><th width="30%"><!--Field-->字段</th><th><!--Description-->描述</th></tr></thead>
<tbody>

<tr><td><code>clientCAFile</code><br/>
<code>string</code>
</td>
<td>
   <!--clientCAFile is the path to a PEM-encoded certificate bundle. If set, any request
presenting a client certificate signed by one of the authorities in the bundle
is authenticated with a username corresponding to the CommonName,
and groups corresponding to the Organization in the client certificate.-->
   <p><code>clientCAFile</code>是一个指向 PEM 编发的证书包的路径。
如果设置了此字段，则能够提供由此证书包中机构之一所签名的客户端证书的请求会被成功认证，
并且其用户名对应于客户端证书的<code>CommonName</code>、组名对应于客户端证书的
<code>Organization</code>。</p>
</td>
</tr>
</tbody>
</table>

## `MemoryReservation`     {#kubelet-config-k8s-io-v1beta1-MemoryReservation}

<!--
**Appears in:**
-->
**出现在：**

- [KubeletConfiguration](#kubelet-config-k8s-io-v1beta1-KubeletConfiguration)

<!--
MemoryReservation specifies the memory reservation of different types for each NUMA node
-->
MemoryReservation 为每个 NUMA 节点设置不同类型的内存预留。

<table class="table">
<thead><tr><th width="30%"><!--Field-->字段</th><th><!--Description-->描述</th></tr></thead>
<tbody>

<tr><td><code>numaNode</code> <B>[必需]</B><br/>
<code>int32</code>
</td>
<td>
   <!--span class="text-muted">No description provided.</span-->
   <p>NUMA 节点</p>
</td>
</tr>

<tr><td><code>limits</code> <B>[必需]</B><br/>
<a href="https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.23/#resourcelist-v1-core"><code>core/v1.ResourceList</code></a>
</td>
<td>
   <!--span class="text-muted">No description provided.</span-->
   <p>资源列表</p>
</td>
</tr>
</tbody>
</table>

## `MemorySwapConfiguration`     {#kubelet-config-k8s-io-v1beta1-MemorySwapConfiguration}

<!--
**Appears in:**
-->
**出现在：**

- [KubeletConfiguration](#kubelet-config-k8s-io-v1beta1-KubeletConfiguration)

<table class="table">
<thead><tr><th width="30%"><!--Field-->字段</th><th><!--Description-->描述</th></tr></thead>
<tbody>

<tr><td><code>swapBehavior</code><br/>
<code>string</code>
</td>
<td>
   <!--swapBehavior configures swap memory available to container workloads. May be one of
&quot;&quot;, &quot;LimitedSwap&quot;: workload combined memory and swap usage cannot exceed pod memory limit
&quot;UnlimitedSwap&quot;: workloads can use unlimited swap, up to the allocatable limit.
   -->
   <p><code>swapBehavior</code>配置容器负载可以使用的交换内存。可以是
   <ul>
    <li>&quot;&quot;、&quot;LimitedSwap&quot;：工作负载的内存和交换分区总用量不能超过 Pod 的内存限制；</li>
    <li>&quot;UnlimitedSwap&quot;：工作负载可以无限制地使用交换分区，上限是可分配的约束。</li>
   </ul>
</td>
</tr>
</tbody>
</table>

## `ResourceChangeDetectionStrategy`     {#kubelet-config-k8s-io-v1beta1-ResourceChangeDetectionStrategy}

<!--
(Alias of `string`)
-->
（`string` 类型的别名）

<!--
**Appears in:**
-->
**出现在：**

- [KubeletConfiguration](#kubelet-config-k8s-io-v1beta1-KubeletConfiguration)

<!--
ResourceChangeDetectionStrategy denotes a mode in which internal
managers (secret, configmap) are discovering object changes.
-->
ResourceChangeDetectionStrategy 给出的是内部管理器（ConfigMap、Secret）
用来发现对象变化的模式。

## `ShutdownGracePeriodByPodPriority`     {#kubelet-config-k8s-io-v1beta1-ShutdownGracePeriodByPodPriority}

<!--
**Appears in:**
-->
**出现在：**

- [KubeletConfiguration](#kubelet-config-k8s-io-v1beta1-KubeletConfiguration)

<!--
ShutdownGracePeriodByPodPriority specifies the shutdown grace period for Pods based on their associated priority class value
-->
ShutdownGracePeriodByPodPriority 基于 Pod 关联的优先级类数值来为其设置关闭宽限时间。

<table class="table">
<thead><tr><th width="30%"><!--Field-->字段</th><th><!--Description-->描述</th></tr></thead>
<tbody>

<tr><td><code>priority</code> <B>[必需]</B><br/>
<code>int32</code>
</td>
<td>
   <!--priority is the priority value associated with the shutdown grace period-->
   <p><code>priority</code>是与关闭宽限期限相关联的优先级值。</p>
</td>
</tr>

<tr><td><code>shutdownGracePeriodSeconds</code> <B>[必需]</B><br/>
<code>int64</code>
</td>
<td>
   <!--shutdownGracePeriodSeconds is the shutdown grace period in seconds-->
   <p><code>shutdownGracePeriodSeconds</code>是按秒数给出的关闭宽限期限。
</td>
</tr>
</tbody>
</table>

## `FormatOptions`     {#FormatOptions}

<!--
**Appears in:**
-->
**出现在：**

- [LoggingConfiguration](#LoggingConfiguration)

<p>
<!--
FormatOptions contains options for the different logging formats.
-->
FormatOptions 包含为不同日志格式提供的选项。
</p>

<table class="table">
<thead><tr><th width="30%"><!--Field-->字段</th><th><!--Description-->描述</th></tr></thead>
<tbody>

<tr><td><code>json</code> <B>[必需]</B><br/>
<a href="#JSONOptions"><code>JSONOptions</code></a>
</td>
<td>
   <p><!--[Experimental] JSON contains options for logging format &quot;json&quot;.-->
   [试验功能] <code>json</code> 包含为 &quot;json&quot; 日志格式提供的选项。
   </p>
</td>
</tr>
</tbody>
</table>

## `JSONOptions`     {#JSONOptions}

<!--
**Appears in:**
-->
**出现在：**

- [FormatOptions](#FormatOptions)

<p>
<!--
JSONOptions contains options for logging format &quot;json&quot;.
-->
JSONOptions 包含为 &quot;json&quot; 日志格式提供的选项。
</p>

<table class="table">
<thead><tr><th width="30%"><!--Field-->字段</th><th><!--Description-->描述</th></tr></thead>
<tbody>
<tr><td><code>splitStream</code> <B>[必需]</B><br/>
<code>bool</code>
</td>
<td>
   <p>
   <!--[Experimental] SplitStream redirects error messages to stderr while
info messages go to stdout, with buffering. The default is to write
both to stdout, without buffering.
   -->
   [试验功能] <code>splitStream</code> 将错误信息重定向到标准错误输出（stderr），
而将提示信息重定向到标准输出（stdout），并为二者提供缓存。
默认设置是将二者都写出到标准输出，并且不提供缓存。
   </p>
</td>
</tr>

<tr><td><code>infoBufferSize</code> <B>[必需]</B><br/>
<a href="https://pkg.go.dev/k8s.io/apimachinery/pkg/api/resource#QuantityValue"><code>k8s.io/apimachinery/pkg/api/resource.QuantityValue</code></a>
</td>
<td>
   <p>
   <!--[Experimental] InfoBufferSize sets the size of the info stream when
using split streams. The default is zero, which disables buffering.-->
   [试验功能] <code>infoBufferSize</coe> 在分离数据流时用来设置提示数据流的大小。
默认值为 0，相当于禁止缓存。
   </p>
</td>
</tr>
</tbody>
</table>

## `LoggingConfiguration`     {#LoggingConfiguration}

<!--
**Appears in:**
-->
**出现在：**

- [KubeletConfiguration](#kubelet-config-k8s-io-v1beta1-KubeletConfiguration)

<!--
LoggingConfiguration contains logging options
Refer [Logs Options](https://github.com/kubernetes/component-base/blob/master/logs/options.go) for more information.
-->
LoggingConfiguration 包含日志选项。
参考 [Logs Options](https://github.com/kubernetes/component-base/blob/master/logs/options.go)
以了解更多信息。

<table class="table">
<thead><tr><th width="30%"><!--Field-->字段</th><th><!--Description-->描述</th></tr></thead>
<tbody>

<tr><td><code>format</code> <B>[必需]</B><br/>
<code>string</code>
</td>
<td>
  <p>
  <!--Format Flag specifies the structure of log messages.
default value of format is `text`-->
  <code>format<code> 设置日志消息的结构。默认的格式取值为 <code>text</code>。
  </p>
</td>
</tr>

<tr><td><code>flushFrequency</code> <B>[必需]</B><br/>
<a href="https://godoc.org/time#Duration"><code>time.Duration</code></a>
</td>
<td>
  <p>
  <!--Maximum number of seconds between log flushes. Ignored if the
selected logging backend writes log messages without buffering.-->
  对日志进行清洗的最大间隔秒数。如果所选的日志后端在写入日志消息时不提供缓存，
则此配置会被忽略。
  </p>
</td>
</tr>

<tr><td><code>verbosity</code> <B>[必需]</B><br/>
<code>uint32</code>
</td>
<td>
  <p>
  <!--Verbosity is the threshold that determines which log messages are
logged. Default is zero which logs only the most important
messages. Higher values enable additional messages. Error messages
are always logged.-->
  <code>verbosity</code> 用来确定日志消息记录的详细程度阈值。默认值为 0，
意味着仅记录最重要的消息。数值越大，额外的消息越多。出错消息总是会被记录下来。
  </p>
</td>
</tr>

<tr><td><code>vmodule</code> <B>[必需]</B><br/>
<a href="#VModuleConfiguration"><code>VModuleConfiguration</code></a>
</td>
<td>
  <p>
  <!--VModule overrides the verbosity threshold for individual files.
Only supported for &quot;text&quot; log format.-->
  <code>vmodule</code> 会在单个文件层面重载 verbosity 阈值的设置。
这一选项仅支持 &quot;text&quot; 日志格式。
  </p>
</td>
</tr>

<tr><td><code>sanitization</code> <B>[必需]</B><br/>
<code>bool</code>
</td>
<td>
  <p>
  <!--[Experimental] When enabled prevents logging of fields tagged as sensitive (passwords, keys, tokens).
Runtime log sanitization may introduce significant computation overhead and therefore should not be enabled in production.)-->
  [试验功能] 当启用此选项时，被标记为敏感的字段（密码、秘钥、令牌）不会被日志记录。
运行时日志过滤功能可能会引入非常大的计算开销，因此在生产环境中不应启用。
  </p>
</td>
</tr>

<tr><td><code>options</code> <B>[必需]</B><br/>
<a href="#FormatOptions"><code>FormatOptions</code></a>
</td>
<td>
  <p>
  <!--[Experimental] Options holds additional parameters that are specific
to the different logging formats. Only the options for the selected
format get used, but all of them get validated.-->
  [试验功能] <code>options</code> 中包含特定于不同日志格式的配置参数。
只有针对所选格式的选项会被使用，但是合法性检查时会查看所有选项配置。
  </p>
</td>
</tr>
</tbody>
</table>

## `VModuleConfiguration`     {#VModuleConfiguration}

<!--
(Alias of `[]k8s.io/component-base/config/v1alpha1.VModuleItem`)
-->
（`[]k8s.io/component-base/config/v1alpha1.VModuleItem` 类型的别名）

<!--
**Appears in:**
-->
**出现在：**

- [LoggingConfiguration](#LoggingConfiguration)

<!--
VModuleConfiguration is a collection of individual file names or patterns
and the corresponding verbosity threshold.
-->
VModuleConfiguration 是一个集合，其中包含一个个文件名（或文件名模式）
及其对应的详细程度阈值。

