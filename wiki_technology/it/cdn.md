### CDN {#cdn}

CDN

1 、 CDN 是什么

CDN （ Content Delivery Network ），就是内容发布网或者内容分发网，它的主要目的：通过在现有的 Internet 中增加一层新的网络架构，将网站的内容发布到最接近用户的网络边缘，使用户可以就近取得所需的内容，从而提高用户访问网站的响应速度，提升用户体验，同时能够分散访问压力，把本来用户集中访问分散到各地去。网站的内容提供商（比如新浪、搜狐、网易等等）使用 CDN ，就可以在宏观层解决一部分大流量、海量用户并发等令人头疼的问题。

2 、 CDN 的组成

内容发布网 (CDN) 是一个经策略性部署的整体系统，包括分布式存储、负载均衡、网络请求的重定向和内容管理４个要件，而内容管理和全局的网络流量管理是 CDN 的核心所在。通过用户就近性和服务器负载的判断， CDN 确保内容以一种极为高效的方式为用户的请求提供服务，达到用户所要求的服务距用户仅有 &quot; 一跳 &quot;(Single Hop) 之遥。

我们通常的内容发布模式都是将网站数据放到一处，然后应对来自世界各地的访问，我们多数考虑的是软件部署架构，很少考虑网络硬件架构。与之形成对比的是， CDN 则强调了网络在内容发布中的重要性。通过引入主动的内容管理层的和全局负载均衡， CDN 从根本上区别于传统的内容发布模式。

内容提供商承担了他们不该干也干不好的内容发布服务。

3 、互联网服务的产业链

纵观整个宽带服务的价值链，内容提供商和用户位于整个价值链的两端，中间依靠网络服务提供商将其串接起来。随着互联网工业的成熟和商业模式的变革，在这条价值链上的角色越来越多也越来越细分，出现了内容运营商、托管服务提供商、骨干网络服务提供商、接入服务提供商等等。在这一条价值链上的每一个角色都要分工合作、各司其职才能为客户提供良好的服务，从而带来多赢的局面。从内容与网络的结合模式上看，内容的发布已经走过了 ICP 的内容（应用）服务器和 IDC 这两个阶段。 IDC 的热潮也催生了托管服务提供商这一角色。但是， IDC 并不能解决内容的有效发布问题。内容位于网络的中心并不能解决骨干带宽的占用和建立 IP 网络上的流量秩序。因此将内容推到网络的边缘，为用户提供就近性的边缘服务，从而保证服务的质量和整个网络上的访问秩序就成了一种显而易见的选择，这就是 CDN 服务模式。 CDN 的建立解决了困扰内容运营商的内容 &quot; 集中与分散 &quot; 的两难选择，无疑对于构建良好的互联网价值链是有价值的，也是不可或缺的最优网站加速服务。

4 、 CDN 服务提供商

ChinaCache 是中国最大的 CDN 服务提供商，是不是唯一未可知也。要想成为 CDN 服务提供商，恐怕要摆平电信、网通、铁通等等运营商，这得需要什么样的能力和背景不得而知。它的服务节点在全球已经超过 130 个，其中国内节点超过 80 个，覆盖全国主要 6 大网络（所谓 6 线机房，就是这么来的）的主要省份，象各大门户网站，比如新浪、网易等等都是租用了他们的服务。所以，你无论是在南方，或者北方，还是在北美，访问这些门户网站，感觉速度都很快，最主要的原因之一就是 CDN 发挥了效果。一般小网站是用不起这服务的，所以慢点就慢点了吧，可以租用互联互通的 6 线机房，如果网络足够宽的话，用户也可以忍受。如果想继续提升用户体验的话，就需要做一些网站镜像，部署在具有代表性的几个大城市，比如华南可以部署在广州，华东可以部署在上海，华北可以部署在北京，不过内容镜像的过程，就需要自己去部署和维护。还有的网站，采用内容分割的方式，比如建立针对各地的分站，业务情况不同，可能部署的策略不同。 CDN 可以认为是基础网络建设的一种策略。

前面介绍了 cdn 的一些原理和概念，以及提供 cdn 基础网络服务的途径。 cdn 看起来对于静态内容的，比如 html,js,image 是非常合适的，通过 cdn 的部署，用户只需要一跳就可以访问到网站的内容。那对于动态内容怎么办呢？我回答一下：

动态内容按照存在形态可以分为三类。

第一类：内容长时间不需变化，这类内容一般是通过网页静化技术，实现动态内容转换成静态内容，从而达到 cdn 部署，典型的就是内容类网站，比如新浪、搜狐、网易等等的内容发布系统 cms ，内容的增删改等管理工作被准实时同步到各个节点。

第二类：内容可能会短时间内发生变动，但是最终会稳定。比如论坛、博客等应用，这类服务提供的内容按照一定的时间间隔，实现批量静化，当然也有实时静化，像 Mop 的大杂烩、网易社区就是使用了这样的策略。

第三类：内容会实时变化，非常个性化。比如邮箱应用，这类服务提供的内容无法实现静化，只能通过实行分区域部署和负载均衡等手段进行优化。

对于提供 cdn 服务的厂商来讲，静态内容的 cdn 自然没有问题，对于第三类服务，只能从通信链路层进行相应的优化。

对于很多网站的伪静化，有的出于 Seo 的考虑，有的出于安全性的考虑，手段基本上是 rewrite Url 。它只不过是一种外在的表现形式，与 Html 静化是两回事，它依然是一种动态内容。