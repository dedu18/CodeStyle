## 一、发现的问题：
#### 项目： 现有项目名混乱、变量和方法等命名虽然驼峰且见名知意，但还是不统一规范、有硬编码魔法值存在、代码不整洁、业务线日志不清晰等
#### 个人：接口初期健壮性不够好，变量命名不够统一标准，日志注释格式不齐，代码还有很大优化空间

## 二、参考书籍：
#### 《clean code-代码整洁之道》、《重构改善既有代码的设计》

## 三、读书收获  
 - 1命名  
&nbsp;&nbsp;&nbsp;&nbsp;  1.1名副其实：代码模糊度：上下文在代码中未被明确体现的程度。<br/><br/>
&nbsp;&nbsp;&nbsp;&nbsp;  1.2避免误导：<br/><br/>
&nbsp;&nbsp;&nbsp;&nbsp;  1.3做有意义的区分：光是使用数字系列或废话做区分远远不够，如Product、ProductInfo、ProductData没意义<br/><br/>
&nbsp;&nbsp;&nbsp;&nbsp;1.4使用读的出来的名称：<br/><br/>
&nbsp;&nbsp;&nbsp;&nbsp;1.5使用可搜索的名称：如变量ey和变量everyyear<br/><br/>
&nbsp;&nbsp;&nbsp;&nbsp;1.6避免使用编码：如加上各种前缀m_、接口不加前导字母I，如AbstractFactory使用ShapeFactory和ShapeFactoryImp，因为不想让用户知道我给他们的是接口<br/><br/>
&nbsp;&nbsp;&nbsp;&nbsp;1.7类名:应该是名词或名词短语，而不应是动词<br/><br/>
&nbsp;&nbsp;&nbsp;&nbsp;1.8方法名:应当是动词或动词短语，如postPayment/deletePage/save，属性访问器、修改器、断言等应该根据其值命名并依造Javabean标准加上get、set、is前缀<br/><br/>
&nbsp;&nbsp;&nbsp;&nbsp;1.9每个概念对应一个词：每个抽象概念选一个词并一以贯之，如fetch/get有啥区别？不要混用，选好一个之后在库中或项目中全都使用这个概念就好。一以贯之命名法也是福音。<br/><br/>
&nbsp;&nbsp;&nbsp;&nbsp;1.10别用双关语：避免将同一个单词用于不同目的。如好多个类中都有add方法，只要这些add方法参数列表和返回值在语义上等价就好。但如果业务语义确实不同，则果断用insert或append之类的词。即便违反了1.8的一以贯之<br/><br/>
&nbsp;&nbsp;&nbsp;&nbsp;1.11添加有意义的语境:当firstName、lastName、state放一起时能知道state是地址相关，但单独使用时则无法判别，此时加上前缀addr组成addrState更好，或者单独封装Address类<br/><br/>
&nbsp;&nbsp;&nbsp;&nbsp;1.12不要加没用语境：如Address类中accountAddress和customerAddress后缀多余，有类名和短名称就已经很清楚了。当然如果是MAC地址和Web地址则使用PostalAddress、MAC、URI更精准。<br/><br/>

 - 2函数  
&nbsp;&nbsp;&nbsp;&nbsp;2.1短小:每个函数大概都只有两行、三行或四行长，每个函数都一目了然，每个函数都只说一件事。if/else/while语句的代码块都只有一行，此行就是函数调用。函数体的缩进层次不应多余两层。<br/><br/>
&nbsp;&nbsp;&nbsp;&nbsp;2.2只做一件事:如果函数只做了该函数名下同一抽象层上的事则还是只做了一件事。只做一件事就是无法再被合理的拆分为多个片段。<br/><br/>
&nbsp;&nbsp;&nbsp;&nbsp;2.3每个函数一个抽象层:要让代码有自顶向下的阅读顺序，每个函数后面都跟着位于下一个抽象层级的代码。即要这样读程序：就像一些列To起头的段落，每个段落都描述当前抽象层级，并引用位于下一抽象层级的后续To起头段落。<br/><br/>
&nbsp;&nbsp;&nbsp;&nbsp;2.4switch语句:尝试使用多态来实现<br/><br/>
&nbsp;&nbsp;&nbsp;&nbsp;2.5使用描述性名称:不要害怕长的函数名称，长而具有描述性的名称总比短而费解的名称好<br/><br/>
&nbsp;&nbsp;&nbsp;&nbsp;2.6函数参数:最理想参数数量是0个，其次是1，再次是2，尽量避免3个，切忌有足够理由才用3个以上参数<br/><br/>
&nbsp;&nbsp;&nbsp;&nbsp;2.7输出参数:应避免使用输出参数，如果函数要修改某种状态，就修改所属对象的状态，如appendFooter(s)和s.appendFooter()<br/><br/>
&nbsp;&nbsp;&nbsp;&nbsp;2.8函数名称指令和询问分隔:如不要set()，而要setAndCheckIfExist()。<br/><br/>
&nbsp;&nbsp;&nbsp;&nbsp;2.9使用异常代替返回错误码，并抽离Try/Catch代码块另外形成函数。<br/><br/>
&nbsp;&nbsp;&nbsp;&nbsp;2.10错误处理就是一件事:如果try存在，则该是这个函数的第一个单词，且catch/finally代码块后面不该有其他内容。<br/><br/>
&nbsp;&nbsp;&nbsp;&nbsp;2.11结构化编程:每个函数、函数中每个代码块都应只有一个入口一个出口，即每个函数中只该有一个return，循环中不能有break或continue。<br/><br/>
&nbsp;&nbsp;&nbsp;&nbsp;2.11如何编写好的函数:写代码就像写文章，先想什么就写什么，然后打磨，初稿也许粗陋无序，你就斟酌推敲直到心中的样子。一开始都冗长复杂，有太多缩进和嵌套循环，过长的参数列表，名称随意或大量重复代码，但如果配上一套单元测试，覆盖代码然后打磨这些代码，分解函数，修改名称，消除重复，同时保持测试通过就好，没人能一开始就按照规则写。<br/><br/>

 - 3注释
 - 4格式
 - 5错误处理  
 &nbsp;&nbsp;&nbsp;&nbsp;5.1统一处理
 - 6单元测试  
&nbsp;&nbsp;&nbsp;&nbsp;6.1单个断言<br/>
&nbsp;&nbsp;&nbsp;&nbsp;6.2每个测试只测试一个概念<br/>
&nbsp;&nbsp;&nbsp;&nbsp;6.3FIRST:快速(First)测试应该够快运行/独立(Independent)测试应该互相独立/可重复(Repeatable)测试应当在任何环境重复通过/自足验证(Self-Validating)测试应有布尔值输出/及时(Timely)测试应及时编写<br/><br/>

 - 3类  
&nbsp;&nbsp;&nbsp;&nbsp;3.1类的组织:遵循标准Java约定，类应该从一组变量列表开始，如有公共静态变量应先出现，然后是私有静态变量以及私有实体变量，很少有公共变量。然后是公共函数，把该公共函数调用的私有函数紧跟其后，满足自顶向下原则。<br/><br/>
&nbsp;&nbsp;&nbsp;&nbsp;3.2类应该短小:①单一职责原则:类或模块应有且只有一条加以修改的理由，系统应该由许多短小的类而不是少量巨大的类组成。每个小类封装一个权责，只有一个修改的原因，并与少数其他类一起协同达到期望的系统行为。②内聚:类应该只有少数实体变量，如果类中的每个变量都被每个方法所使用，则此类具有最大的内聚性，反之则应分拆到更多类中。<br/><br/>

 - 4重构案例  
&nbsp;&nbsp;&nbsp;&nbsp;4.1简介:重构技术就是以微小的步伐修改程序。如果有了一套可靠的测试案例机制，即便你犯下错误，也会很容易便可发现它。【任何一个傻瓜都能写出计算机可以理解的代码。唯有写出人类容易理解的代码，才是优秀的程序员。】<br/><br/>
&nbsp;&nbsp;&nbsp;&nbsp;4.2节奏:测试、小修改、测试、小修改······这种节奏让重构得以快速而安全的前进<br/><br/>

 - 5重构原则  
&nbsp;&nbsp;&nbsp;&nbsp;5.1Duplicated Code重复代码:如果在一个以上地点看到相同程序结构，就设法将它们合而为一。如同一个类的两个函数含有相同表达式、互为兄弟的子类内含相同表达式、毫不相关的类出现重复代码。<br/><br/>
&nbsp;&nbsp;&nbsp;&nbsp;5.2Long Method过长函数:程序越长越难理解，每当感觉需要以注释说明点什么的时候就把需要说明的东西写进一个独立函数中，并以其用途（而非实现手法）命名，即便有时会只有一行或调用动作比函数自身还长。条件表达式和循环常常也是可以提炼。<br/><br/>
&nbsp;&nbsp;&nbsp;&nbsp;5.3Large Class过大的类:如果利用单个类做太多事情其内往往就会出现太多实例变量，一旦如此就可使用[5.1]处理。如果类内有太多代码重复、混乱则进行提取。<br/><br/>
&nbsp;&nbsp;&nbsp;&nbsp;5.4Long Parameter List过长参数列:使用对象，只需传给函数足够的，能让函数从中获得自己所需的东西即可。<br/><br/>
&nbsp;&nbsp;&nbsp;&nbsp;5.5Divergent Change发散式变化:如果某个类经常因为不同的原因在不同的方向上发生变化，则应是发散性变化。针对某一外界变化的所有相应修改，都只应该发生在单一类中，而这个新类内的所有内容都应该反应此变化，为此应找出某特定原因而造成的所有变化然后将它们提炼到另一个类中。<br/><br/>
&nbsp;&nbsp;&nbsp;&nbsp;5.6Shotgun Surgery散弹式修改:与【5.5】相反，如果遇到某个变化，都必须在许多不同的类内做许多小修改，则需要把所有需要修改的代码放进同一个类，如果没有合适的类可放置则新建一个，否则修改的代码散布四处很难找到且易漏。<br/><br/>
&nbsp;&nbsp;&nbsp;&nbsp;5.7......:<br/><br/>

 - 6测试体系 
&nbsp;&nbsp;&nbsp;&nbsp;6.1测试的价值:类应该包含它们自己的测试代码。切勿着迷于增量式开发，尝试在结束每次增量时为每个类添加测试，然后需要做的就是把期望结果放进测试代码中，一切都没问题就输出一个OK即可。<br/><br/>
&nbsp;&nbsp;&nbsp;&nbsp;6.2测试编写时机:最有用的时机是在开始编程之前。编写测试代码其实就是在问自己这个功能需要做什么，预先写好的测试代码也是一个明确的结束标志，一旦测试代码正常运行，则工作结束。而对于重构，就必须编写测试代码。可使用assert或JUnit的Assert.assertEquals()<br/><br/>

 - 7重新组织函数  
&nbsp;&nbsp;&nbsp;&nbsp;7.1Extract Method提炼函数:①创造一个新函数，根据函数意图来命名，以它做什么来命名，而不是怎样做命名，如果想不到更有意义的名称，就别动。②无局部变量情况直接复制粘贴并插入函数调用动作即可。③有局部变量且目标函数仅是读取则简单地将这些变量当作参数传入函数。必要的话可以处理多个源函数的局部变量参数。④有局部变量且变量仅在目标函数中使用则可以把这些局部变量直接提炼到目标函数中。这样可以帮助减少局部变量。⑤有局部变量且变量在目标函数内和外都使用，则在目标函数中修改返回改变后的值。<br/><br/>
&nbsp;&nbsp;&nbsp;&nbsp;7.2Inline Method内联函数:①如果函数确定不具有多态性且函数本地和名称同样清楚易懂，则直接将函数体插入到调用处。<br/><br/>
&nbsp;&nbsp;&nbsp;&nbsp;7.3Inline Temp内联临时变量:①如果有一个临时变量仅被简单表达式赋值一次，则将用到它的地方直接替换为对它赋值的表达式本身。（可先将它声明为final确保编译没问题）<br/><br/>
&nbsp;&nbsp;&nbsp;&nbsp;7.4Replace Temp With Query以查询取代临时变量:①如果程序以一个临时变量保存某一表达式的运算结果，将这个表达式提炼到一个独立函数中，将变量引用替换为函数调用，这样新函数就可被复用，利用提炼函数【7.1】。当然有时简单的话可以直接内联临时变量【7.3】<br/><br/>
&nbsp;&nbsp;&nbsp;&nbsp;7.5Split Variable分解临时变量:①如有某个临时变量被赋值多次，且既不是循环变量也不用于收集结果，可针对每次赋值创造独立、对应的临时变量。否则变量就承担了多个任务。<br/><br/>
&nbsp;&nbsp;&nbsp;&nbsp;7.6Remove Assignments To Parameters移除对参数的赋值:①在函数中，对于值传递，以一个临时变量取代该参数出现的位置。可在函数参数中使用final约束。
<br/><br/>
&nbsp;&nbsp;&nbsp;&nbsp;7.7Replace Method With Method Object以函数对象取代函数:①将大型函数放进一个对象中，如此一来局部变量就成了对象内字段，就可在一个对象中将大型函数分解。
&nbsp;&nbsp;&nbsp;&nbsp;7.8Substitute Algorithm替换算法:①如果想将某个算法替换为另一个更清晰的算法，则将函数本体替换为另一个更简单的算法。
<br/><br/>

 - 8在对象之间搬移特性  
&nbsp;&nbsp;&nbsp;&nbsp;8.1Move Method搬移函数:①如果一个类有太多行为，或一个类与另一个类有太多合作而耦合，则在这个函数最多应用的类中创建一个类似行为的函数并将代码复制，且旧函数变成单纯的引用委托函数，或是直接删除。
<br/><br/>
&nbsp;&nbsp;&nbsp;&nbsp;8.2Move Field搬移字段:①如果一类中某个字段被其他类更多的引用，则直接将这个字段搬到那个类中，并修改源类引用新字段（先看是否有现成字段和函数可帮助获得新字段值，没有则看是否可以新建函数帮助获取。）。
<br/><br/>
&nbsp;&nbsp;&nbsp;&nbsp;8.3Extract Class提炼类:①如果一个类做了本应两个类做的事情，则新建一个类，将相关字段和函数从旧类搬移到新类。
<br/><br/>
&nbsp;&nbsp;&nbsp;&nbsp;8.4Inline Class将类内联化:①如果某个类没有做太多事情，则将这个类的所有特性搬移到另一个类中并删除原类。
<br/><br/>
&nbsp;&nbsp;&nbsp;&nbsp;8.5Hide Delegate隐藏委托关系:①如果客户通过一个委托类来调用另一个对象，则在这个服务类上建立客户所需的所有函数并隐藏委托关系。
<br/><br/>
&nbsp;&nbsp;&nbsp;&nbsp;8.6Remove Hiddle Man移除中间人:①如果某个类做了太多的简单委托动作，则让客户直接调用受托类。
<br/><br/>

 - 9重新组织数据 
&nbsp;&nbsp;&nbsp;&nbsp;9.1Self Encapsulate Field自封装字段:①为对象创建Getter和Setter函数并通过这些函数访问字段。
<br/><br/>
&nbsp;&nbsp;&nbsp;&nbsp;9.2Replace Data Value With Object以对象取代数据值:①有时某些数据关联性较大时，可将这些数据项封装成一个对象。
<br/><br/>
&nbsp;&nbsp;&nbsp;&nbsp;9.3Change Value To Reference将值对象改成引用对象:①如果某个对象被多个其他对象引用，且该对象数据都是一样的，则可将该对象构造方法私有化并提供一个工厂方法如create()，然后创建缓存如HashMap保存加载好的对象，对象加载可在静态方法块中执行，然后在工厂方法中返回既存的对象。
<br/><br/>
&nbsp;&nbsp;&nbsp;&nbsp;9.4Change Reference To Value将引用对象改成值对象:①与【9.3】相反，如果一个引用对象很小且是不可变对象，则考虑删除工厂方法并将构造函数声明为public，并重写equals和hashCode函数。
<br/><br/>
&nbsp;&nbsp;&nbsp;&nbsp;9.5Replace Array With Object以对象取代数组:①如果有一个数组，如字符串数组，其中的元素各代表不同的东西，则考虑将这个数组封装成一个对象。
<br/><br/>
&nbsp;&nbsp;&nbsp;&nbsp;9.6Duplicate Observed Data复制被监视的对象:①将数据展示与数据计算逻辑分离开来，将数据展示里的数据复制一份到数据计算逻辑中，并使用观察者Observer模式维护两份数据的一致性。这样数据计算的修改就不会影响数据展示。
<br/><br/>
&nbsp;&nbsp;&nbsp;&nbsp;9.7Replace Magic Number With Symbolic Constant以字面常量取代魔法数:①如果一个字面数值有特别含义，则创造一个常量并根据意义命名以取代那个魔法数。
<br/><br/>
&nbsp;&nbsp;&nbsp;&nbsp;9.8Encapsulate Field封装字段:①如果类中有public字段，则将其改成private并提供相应的访问方法。
<br/><br/>
&nbsp;&nbsp;&nbsp;&nbsp;9.9Encapsulate Collection封装集合:①如果一个函数返回集合，则让该函数返回集合的只读副本并在这个类中提供添加/移除集合元素的函数。因为如果不这样会让集合拥有着无法控制集合本身且对用户暴露太多对象内部数据。
<br/><br/>
&nbsp;&nbsp;&nbsp;&nbsp;9.10Replace Type Code With Subclasses:①如果类中有一个不可变的类型码如枚举值，它会影响类的行为，则以子类取代这个类型码。这是多态的体现。处理Switch和if-else-if语句需要这样做。
<br/><br/>
&nbsp;&nbsp;&nbsp;&nbsp;9.11Replace Type Code With State/Strategy:①如果一个类型码会影响类的行为且无法通过继承手段消除，则以状态对象取代类型码。
<br/><br/>
&nbsp;&nbsp;&nbsp;&nbsp;9.12Replace Subclass With Fields以字段取代子类:①如果各个子类的唯一区别就是返回常量数据的函数上，则删除子类，并在父类中增加字段用以区别，使得函数直接返回这些字段。
<br/><br/>

 - 10简化条件表达式  
&nbsp;&nbsp;&nbsp;&nbsp;10.1Decompose Conditional分解条件表达式:①如果有一个复杂的if-then-else语句，则从if/then/else三个段落中分别提炼成独立函数。
<br/><br/>
&nbsp;&nbsp;&nbsp;&nbsp;10.2Consolidate Conditional Expression合并条件表达式:①如果多个if返回的结果都相同，则将这些全部合并并提炼为一个独立函数。
<br/><br/>
&nbsp;&nbsp;&nbsp;&nbsp;10.3Consolidate Duplicate Conditional Framents合并重复的条件片段:①如果几个条件中有相同的语句代码，则将这些代码搬移到条件语句之外。这样能清晰表示哪些因条件而变化。
<br/><br/>
&nbsp;&nbsp;&nbsp;&nbsp;10.4Replace Nested Conditional With Guard Clauses用卫语句取代嵌套条件表达式:①卫语句就是把复杂的条件表达式拆分成多个条件表达式，比如一个很复杂的表达式，嵌套了好几层的if-then-else语句，转换为多个if语句，实现它的逻辑，这多条的if语句就是卫语句。if语句可使用卫语句减少层级嵌套。
<br/><br/>
&nbsp;&nbsp;&nbsp;&nbsp;10.5Replace Conditional With Polymorphism以多态取代条件表达式:①如果有个条件表达式是根据对象的类型不同而选择不同的行为，则将这个表达式的每个分支放进一个子类内的覆写函数中，然后将原始函数声明为抽象函数。这样可以处理类型码的switch语句和基于类型名称的if-then-else语句。但这个改造必须有一个继承结构，如果没有的话现在就需要建立。
<br/><br/>
&nbsp;&nbsp;&nbsp;&nbsp;10.6Introduce Null Object引入Null对象:①在很多需要判断==null的地方引入Null对象，也可以是Null接口，里面有isNull函数，这样就可以用函数替换==null判断。
<br/><br/>

 - 11简化函数调用  
<br/><br/>
&nbsp;&nbsp;&nbsp;&nbsp;11.1Rename Method函数改名:①如果函数的名称不能阐述其用途就修改这个函数的名字。
<br/><br/>
&nbsp;&nbsp;&nbsp;&nbsp;11.2Add Parameter添加参数:①如果某个函数需要从调用端获取更多信息，则为这个函数添加一个对象参数让此对象参数携带参数。
<br/><br/>
&nbsp;&nbsp;&nbsp;&nbsp;11.3Remove Parameter移除参数:①如果函数体不再需要某个参数则将这个参数移除掉。
<br/><br/>
&nbsp;&nbsp;&nbsp;&nbsp;11.4Separate Query From Modifier将查询函数与修改函数分离:①如果某个函数既返回对象状态值又修改对象状态，则将这个函数一分为二，一个负责查询，一个负责修改，可额外新增一个函数将这两个函数包裹。
<br/><br/>
&nbsp;&nbsp;&nbsp;&nbsp;11.5Encapsulate Downcast封装向下转型:①如果函数返回的对象需要强制类型转换，则在函数中进行转换，而不要让调用者得到返回值后自己执行类型转换，这样可以向用户隐藏细节。
<br/><br/>
&nbsp;&nbsp;&nbsp;&nbsp;11.6Replace Error Code With Exception以异常取代错误码:①如果函数返回某个特定的代码用以表示某种错误情况，则直接改成异常抛出。
<br/><br/>
&nbsp;&nbsp;&nbsp;&nbsp;11.7Replace Exception With Test以测试取代异常:①参照【11.6】，异常通常是用在异常的、不符合常规行为的地方，而不是替代if检查，如果希望在合理调用前检查一下某个条件，就用if而不是异常。
<br/><br/>


 - 12处理继承关系  
&nbsp;&nbsp;&nbsp;&nbsp;12.1Pull up Field字段上移:①如果子类拥有相同的字段，就将这些字段移到超类中。
<br/><br/>
&nbsp;&nbsp;&nbsp;&nbsp;12.2Pull up Method函数上移:①如果有些函数在各个子类中行为一致，则上移到超类中，可以得话，将它们声明为模板函数。
<br/><br/>
&nbsp;&nbsp;&nbsp;&nbsp;12.3Pull up Constructor Body构造函数本体上移:①如果各个子类中的构造函数行为一致，则将它们上移动到超类中，并在子类中调用它们。
<br/><br/>
&nbsp;&nbsp;&nbsp;&nbsp;12.4Push down Method函数下移:①如果某些函数只与部分子类有关，则将它们移到那些相关子类中。
<br/><br/>
&nbsp;&nbsp;&nbsp;&nbsp;12.5Push down Field字段下移:①如果某些字段只与部分子类有关，则将它们移到那些相关子类中。
<br/><br/>
&nbsp;&nbsp;&nbsp;&nbsp;12.6Extract Subclass提炼子类:①如果类的某些特性只被部分实例用到，则新建一个子类并将那些特性移到这个子类中。
<br/><br/>
&nbsp;&nbsp;&nbsp;&nbsp;12.7Extract Superclass提炼超类:①如果两个类有相似特性，则为这两个类创建一个超类并移动相似特性到超类中。
<br/><br/>
&nbsp;&nbsp;&nbsp;&nbsp;12.8Extract Interface提炼接口:①如果两个类的接口有相同或客户端只使用了类的部分子集，则提炼它们到独立接口中。
<br/><br/>
&nbsp;&nbsp;&nbsp;&nbsp;12.9Collapse Hierarchy折叠继承体系:①如果类与子类无太大差别，则将它们合为一体。
<br/><br/>
&nbsp;&nbsp;&nbsp;&nbsp;12.10Form Template Method塑造模板方法:①如果某些类函数行为一致但又有细微差别，则将它们定义为抽象方法提炼到超类中组成模板方法。
<br/><br/>
&nbsp;&nbsp;&nbsp;&nbsp;12.11Replace Inheritance With Delegation以委托取代继承:①如果子类只需要超类接口中的一部分或根本不需要继承而来的数据，则在子类中创建一个父类的引用，然后修改所有继承的函数改成调用引用的函数，最后去掉继承关系。这样就完成了委托关系。
<br/><br/>
&nbsp;&nbsp;&nbsp;&nbsp;12.12Replace Delegation With Inheritance以继承取代委托:①如果两个类之间是委托关键，但经常需要为整个接口增加很多简单的委托函数，则让委托类继承受托类。
<br/><br/>

 - 13大型重构  
&nbsp;&nbsp;&nbsp;&nbsp;13.1Tease Apart Inheritance梳理并分解继承体系:①如果某个继承体系同时承担两个责任，则建立两个继承体系并通过委托关系让一个可以调用另一个。
<br/><br/>
&nbsp;&nbsp;&nbsp;&nbsp;13.2Convert Procedural Design To Objects将过程化设计转换为对象设计:①如果有一些传统过程化风格的代码，则将数据记录变成数据对象，将大块行为分成小块，并将行为移入相关数据对象之中，最后移除这种过程化风格的类。
<br/><br/>
&nbsp;&nbsp;&nbsp;&nbsp;13.3Extract Hierarchy提炼继承体系:①如果有个类做了太多的工作，其中一部分工作是以大量条件表达式完成的，则建立继承体系，以一个子类表示一种特殊情况。
<br/><br/>

## 四、后献上面向对象的三大基本特征  
#### 封装、继承、多态
封装的目的是隐藏事务内部的实现细节，以便提高安全性和简化编程。封装提供了合理的边界，避免外部调用者接触到内部的细节。我们在日常开发中，因为无意间暴露了细节导致
的难缠bug太多了，比如在多线程环境暴露内部状态，导致的并发修改问题。从另外一个角度看，封装这种隐藏，也提供了简化的界面，避免太多无意义的细节浪费调用者的精力。  

继承是代码复用的基础机制，类似于我们对于马、白马、黑马的归纳总结。但要注意，继承可以看作是非常紧耦合的一种关系，父类代码修改，子类行为也会变动。在实践中，过度
滥用继承，可能会起到反效果。  

多态，你可能立即会想到重写（override）和重载（overload）、向上转型。简单说，重写是父子类中相同名字和参数的方法，不同的实现；重载则是相同名字的方法，但是不同的
参数，本质上这些方法签名是不一样的，


IDEA代码重构Refactor
IDEA变量命名OnlineSearch CODEIF


## 六、代码精进之路 从码农到工匠
- 6.1命名  
&nbsp;&nbsp;&nbsp;&nbsp;6.1.1变量名：应当是名词，能正确描述业务有表达力  
&nbsp;&nbsp;&nbsp;&nbsp;6.1.2函数名：要具体，空泛的命名无意义，要描述做什么，而不是怎么做。如proceddData()就不是一个好的命名，因为所有的方法都是处理数据。相比之下validataUserCredentials()就很好。  
&nbsp;&nbsp;&nbsp;&nbsp;6.1.3类名：通常将类分为实体类和辅助类。实体类承载了核心业务数据和核心业务逻辑，辅助类是辅佐实体类一起完成业务逻辑，如实体类Customer和辅助类CustomerController控制器辅助类和CustomerService服务辅助类。  
&nbsp;&nbsp;&nbsp;&nbsp;6.1.4一致性：要保持命名一致性，每个概念对应一个词并一以贯之，如新增对应create/添加对应add/删除对应remove/修改对应update/查询单个对应get/查询多个对应list/分页对应page/统计对应conut  
&nbsp;&nbsp;&nbsp;&nbsp;6.1.5后置限定词：如果程序中有表示计算结果的变量，如总额、平均值、最大值等，如果要用Total/Sum/Average等限定词来修改某个命名，则把限定词放到名字的后面。如expenseTotal总支出、revenueTotal总收入。  
&nbsp;&nbsp;&nbsp;&nbsp;6.1.6注释：注释不要复述功能，这样没有用，要多解释背后的意图，比如注释“这里等待2秒”和没写一样，不如改成“休息2秒，为了等待关联系统处理结果”。  
- 6.2日志  
&nbsp;&nbsp;&nbsp;&nbsp;6.2.1日志级别：详细的日志输出级别分为OFF、FATAL、ERROR、WARN、INFO、DEBUG、ALL或者自定义的级别。比较有用的4个级别依次是ERROR、WARN、INFO和DEBUG。  
&nbsp;&nbsp;&nbsp;&nbsp;6.2.2Error级别：ERROR表示不能自己恢复的错误，需要立即被关注和解决。ERROR要接入监控和报警系统。ERROR需要人工介入处理，及时止损，否则会影响系统的可用性。当然也不能滥用ERROR，否则就会出现“狼来了”的情况。  
&nbsp;&nbsp;&nbsp;&nbsp;6.2.Warn级别：对于可预知的业务问题，最好不要用ERROR输出日志，以免污染报警系统。例如，参数校验不通过、没有访问权限等业务异常，就不应该用ERROR输出。　　
&nbsp;&nbsp;&nbsp;&nbsp;6.2.Info级别：用于记录系统的基本运行过程和运行状态。通常根据INFO日志可初步定位，主要包括系统状态变
化日志、业务流程的核心处理、关键动作和业务流程的状态变化。适当的INFO可以协助我们排查问题，但是切忌把INFO当成DEBUG使用。
&nbsp;&nbsp;&nbsp;&nbsp;6.2.Debug级别：输出调试信息，如request/response的对象内容。  
 -6.3异常
&nbsp;&nbsp;&nbsp;&nbsp;6.3.1统一异常处理：有统一的异常处理规范，切勿代码中到处充斥着异常捕获的try/catch的代码，搞乱了代码结
构，把错误处理与正常流程混为一谈，严重影响了代码的可读性。有的场景对外直接抛出异常，有的场景对外返回错误码，会增加了服务的使用成本和沟通成本。
&nbsp;&nbsp;&nbsp;&nbsp;6.3.2业务异常和系统异常：建议在业务系统中设定两个异常，分别是BizException（业务异常）和SysException（系统异常），而且这两个异常都应该是Unchecked Exception。针对业务异常和系统异常要做统一的异常处理，类似于AOP，在应用处理请求的切面上进行异常处理收敛。  
```
	try {
		 //业务处理
		 Response res = process(request);
	} catch (BizException e) {
		//业务异常使用WARN级别
		logger.warn("BizException with error code:{},error message:{}", e.getErrorCode(), e.getErrorMsg());
	} catch (SysException ex) {
		//系统异常使用ERROR级别
		log.error("System error" + ex.getMessage(), ex);
	} catch (Exception ex) {
		//兜底
		log.error("System error" + ex.getMessage(), ex);
	}
```  
&nbsp;&nbsp;&nbsp;&nbsp;6.3.3错误码：针对不同错误类型，可以参考做如下约定：P代表参数异常（ParamException）、B代表业务异常（BizException）、S代表系统异常（SystemException）。例如参数异常P_XX_XX  P_Customer_NameIsNull（客户姓名不能为空）/业务异常B_XX_XX  B_Customer_NameAlreadyExist（客户姓名已存在）/系统异常S_XX_XX  S_Unknow_Error（未知系统错误）
- 6.4函数  
&nbsp;&nbsp;&nbsp;&nbsp;6.4.1函数封装：对于if或者while语句中的布尔逻辑，如果条件较为复杂，可将其作为函数抽离出来，用函数名把判断条件的语义显性化表达出来，提高代码可读性。  
&nbsp;&nbsp;&nbsp;&nbsp;6.4.2函数参数与函数体：函数参数应尽可能少，应尽量避免3个以上参数，且函数体应尽可能小，建议一个方法不要超过20行代码。 
&nbsp;&nbsp;&nbsp;&nbsp;6.4.3职责单一：一个方法只做一件事，因为职责越单一，功能越内聚，就越有可能被复用，这和代码的行数没有直接的关联性，但是有间接的关联性。  
&nbsp;&nbsp;&nbsp;&nbsp;6.4.4精简辅助代码：辅助代码（Assistant Code），是程序运行中必不可少的代码，但又不是处理业务逻辑的核心代码，比如判空、打印日志等。这些代码往往会在多个函数中重复冗余，减少辅助代码可以让代码显得更加干净整洁，易于维护。①优化判空可以使用Optional类处理。②优雅降级可以使用Spring Cloud Hystrix的解决方案。  
&nbsp;&nbsp;&nbsp;&nbsp;6.4.5组合函数模式：组合函数要求所有的公有函数（入口函数）读起来像一系列执行步骤的概要，而这些步骤真正的实现细节是在私有函数里面。即将细节封装成函数，外层直接调用，像剥洋葱一样，一层一层。  
&nbsp;&nbsp;&nbsp;&nbsp;6.4.6抽象层次一致性SLAP：这是和组合函数密切相关的一个原则。组合函数要求将一个大函数拆成多个子函数的组合，而SLAP要求函数体中的内容必须在同一个抽象层次上。如果高层次抽象和底层细节杂糅在一起，就会显得凌乱，难以理解。满足SLAP实际上是构筑了代码结构的金字塔。金字塔结构是一种自上而下的结果，在构筑金字塔的过程中，要求金字塔的每一层要属于同一个逻辑范畴、同一个抽象层次。  
&nbsp;&nbsp;&nbsp;&nbsp;6.4.7函数式编程：函数式编程和面向对象编程并没有本质上的区别，在函数式编程
中，函数可以作为参数被其他函数调用在某些场景下可以让代码变得更加简洁、优雅。  
- 6.5设计原则  
&nbsp;&nbsp;&nbsp;&nbsp;6.5.1 SOLID：
Single Responsibility Principle（SRP）：单一职责原则；Open Close Principle（OCP）：开闭原则；Liskov Substitution Principle（LSP）：里氏替换原则；Interface Segregation Principle（ISP）：接口隔离原则；Dependency Inversion Principle（DIP）：依赖倒置原则。  
- 6.6设计模式  
&nbsp;&nbsp;&nbsp;&nbsp;6.6.1创建型模式：用于描述“怎样创建对象”，其特点是“将对象的创建与使用分离”。 
&nbsp;&nbsp;&nbsp;&nbsp;6.6.2结构型模式：用于描述如何将类或对象按某种布局组成更大的结构。  
&nbsp;&nbsp;&nbsp;&nbsp;6.6.3行为型模式：用于描述类或对象之间怎样相互协作共同完成单个对象无法单独完成的任务，以及怎样分配职责。  
- 6.7模型  
&nbsp;&nbsp;&nbsp;&nbsp;6.7.1软件开发：软件开发过程就是问题空间到解决方案空间的一个映射转化。在问题空间中，主要是找出某个业务面临的挑战及其相关需求场景用例分析；而在解决方案空间中，则通过具体的技术工具手段来进行设计实现。就软件系统来说，“问题空间”就是系统要解决的“领域”问题。因此，也可以简单理解为一个领域就对应一个问题空间，是一个特定范围边界内的业务需求的总和。“领域模型”就是“解决方案空间”，是针对特定领域里的关键事物及其关系的可视化表现，是为了准确定义需要解决问题而构造的抽象模型，是业务功能场景在软件系统里的映射转化，其目标是为软件系统的构建统一的认知。
&nbsp;&nbsp;&nbsp;&nbsp;6.7.2领域驱动设计：英文全称为Domain Driven Design，简称DDD。DDD的革命性在于领域驱动设计是面向对象分析的方法论。DDD概念中，实体不仅仅是数据的集合地，还加上了操作数据的行为。不同于由数据驱动的过程式编程中，实体近是数据的集合。通过DDD的战略设计和战术设计，我们可以为问题域划分出合适的子域，并对域中的业务进行建模。
&nbsp;&nbsp;&nbsp;&nbsp;6.7.3 ORM：领域模型和数据模型并不是一一对应的关系，为了弥补二者之间的差异，行业先驱们做了很多关于映射工作的尝试，例如对象关系映射（Object Relationship Mapping，ORM）。ORM的问题在于它太理想化，期望通过工具把数据建模和领域建模合一，这样的尝试注定是很难成功的。