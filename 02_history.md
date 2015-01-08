# 发展历史
早在2000年，CollabNet,Inc就开始寻找CVS替代产品的开发人员。

CollabNet提供了一个名为CollabNet企业版（CEE）的协作软件套件。

这个软件套件的一个组成部分就是版本控制系统。尽管CEE在最初采用了CVS作为其版本控制系统，但是CVS的局限性从一开始就很明显，CollabNet知道，迟早要找到一个更好的替代品。

遗憾的是，CVS已经成为开源世界事实上的标准，很大程度上是因为没有更好的替代品，至少是没有可以自由使用的替代品。

所以CollabNet决定从头编写一个新的版本控制系统，这个系统保留CVS的基本思想，但是要修正其中错误和不合理的特性。

2000年2月，他们联系到OpenSource Development with CVS(Coriolis,1999)的作者Karl Fogel，并且询问他是否希望为这个新项目工作。

巧合的是，当时Karl正在与朋友Jim Blandy讨论设计一个新的版本控制系统。

1995年时，他们两人曾经开办了一个提供CVS支持的公司CyclicSoftware，尽管他们最终卖掉了公司，但还是天天使用CVS进行日常工作。

使用CVS时的挫折促使Jim认真的思考如何管理版本化的数据，并且他当时不仅使用了“Subversion”这个名字，并且已经完成了Subversion版本库的最初设计。

所以当CollabNet提出邀请的时候，Karl马上同意为这个项目工作，同时Jim也找到了他的雇主—RedHat软件公司—允许他到这个项目工作，并且没有限定最终的期限。

CollabNet雇佣了Karl和BenCollinsSussman，详细设计工作从三月开始，在Behlendorf、CollabNet、JasonRobbins和GregStein（当时是一个独立开发者，活跃在WebDAV/DeltaV系统规范制订工作中）恰到好处的激励下，Subversion很快吸引了许多活跃的开发者，结果是许多对CVS有过失望经历的人很乐于为这个项目做些事情。
          
最初的设计小组设定了简单的开发目标。他们不想在版本控制方法学中开垦处女地，他们只是希望修正CVS。

他们决定Subversion应符合CVS的特性，并保留相同的开发模型，但不再重复CVS的一些显著缺陷。     

尽管Subversion并不需要成为CVS的完全替代品，但它应该与CVS保持足够的相似性，以使CVS用户可以轻松的转移到Subversion上。

经过14个月的编码，2001年8月31日，Subversion能够“自己管理自己”了，开发者停止使用CVS保存Subversion的代码，而使用Subversion本身。

虽然CollabNet启动了这个项目，并且一直提供了大量的工作支持（它为一些全职的Subversion开发者提供薪水），但Subversion像其它许多开源项目一样，被松散的、透明的规则管理着，这样的规则激励着知识界的精英们。

CollabNet的版权许可证完全符合Debian的自由软件方针。

也就是说，任何人都可以根据自己的意愿自由的下载、修改和重新发布Subversion，不需要CollabNet或其他人的授权。