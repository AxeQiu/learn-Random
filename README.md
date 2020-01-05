# learn-Random

* **An instance of this class is used to generate a stream of pseudorandom numbers. The class uses a 48-bit seed, which is modified using a linear congruential formula. (See Donald Knuth, The Art of Computer Programming, Volume 2, Section 3.2.1.)**

* Random类使用 (a * sed - b) % n 的计算生成(伪)随机数.其中n为2的48次方; 

* **If two instances of Random are created with the same seed, and the same sequence of method calls is made for each, they will generate and return identical sequences of numbers. In order to guarantee this property, particular algorithms are specified for the class Random. Java implementations must use all the algorithms shown here for the class Random, for the sake of absolute portability of Java code. However, subclasses of class Random are permitted to use other algorithms, so long as they adhere to the general contracts for all the methods.**

* 为保证Java的绝对可移植性, Random类对于相同种子所产生的(伪)随机数数列一定相同.然而Random的子类可以采用不同的随机数生成算法

* **The algorithms implemented by class Random use a protected utility method that on each invocation can supply up to 32 pseudorandomly generated bits.**

* Random类使用protect int next(int bits)方法计算最高为32位的伪随机数. Random的子类可以覆盖该方法, 从而提供其它的随机数生成算法. 参考The Art of Computer Programming**, Volume 3: Seminumerical Algorithms

* **Many applications will find the method Math.random() simpler to use.**

* Math类的random方法, 在第一次被调用时生成一个Random类实例, 并且后续调用Math.random()方法都使用这个实例

* **Instances of java.util.Random are threadsafe. However, the concurrent use of the same java.util.Random instance across threads may encounter contention and consequent poor performance. Consider instead using ThreadLocalRandom in multithreaded designs.**

* Random类是线程安全的. 但是在多线程争用的情况下性能会有所降低. 考虑使用 ThreadLocalRandom类来代替

* **nstances of java.util.Random are not cryptographically secure. Consider instead using SecureRandom to get a cryptographically secure pseudo-random number generator for use by security-sensitive applications.**

* Random类的随机数生成不能应用于安全领域. 使用SecureRandom类来代替

* **关于SecureRandom类**

* **A cryptographically strong random number minimally complies with the statistical random number generator tests specified in FIPS 140-2, Security Requirements for Cryptographic Modules, section 4.9.1. Additionally, SecureRandom must produce non-deterministic output. Therefore any seed material passed to a SecureRandom object must be unpredictable, and all SecureRandom output sequences must be cryptographically strong, as described in RFC 1750: Randomness Recommendations for Security.**

* SecureRandom必须满足"产生不可预测"的(伪)随机数, 并且所有SecureRandom输出序列必须具有加密强度

* **Many SecureRandom implementations are in the form of a pseudo-random number generator (PRNG), which means they use a deterministic algorithm to produce a pseudo-random sequence from a true random seed. Other implementations may produce true random numbers, and yet others may use a combination of both techniques.**

* SecureRandom的实现可以采用: 1.通过使用真随机数产生的种产生的伪随机数.   2.使用真正的随机数     3.两者兼用
