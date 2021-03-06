# Single Vs. Double Dispatcher

Single dispatch is when the call to a function or a method is determined at compile time based on the arguments and return type of the function being called. An example of single dispatch is shown below

```
 public class SingleDispatch
    {
        public class NetworkShare{
            public bool Connect(){
                Console.WriteLine("Connect!");
                return true;
            }

            public int Connect(int timeout){
                Console.WriteLine($"Connect but timeout after {timeout} seconds");
                return timeout;
            }
        }

        public class SingleDipatchTest{
            
            [Fact]
            public void ConnectTest(){
                int timeout = 15 * 60;
                var networkShare = new NetworkShare();
                Assert.Equal(true, networkShare.Connect());
                Assert.Equal(timeout, networkShare.Connect(timeout));
            }
        }
    }
```

In above code, calls to `Connect` methods were predefined at compile time and a concrete implementation of method was invoked. That mechanism is known as Single Dispatching.

Whereas, in Double Dispatch, the invoked method is determined at run time based on the type of concrete instance that is being used to call the method. A sample of double dispatch is given below:

```
public class DoubleDispatchSample
    {
        public abstract class DataShare{
            public abstract string Connect();
        } 

        public class FileShare : DataShare{
            public override string Connect(){
                return "Connected to File Share";
            }
        }
        public class NetworkShare : DataShare{
            public override string Connect(){
                return "Connected to Network Share";
            }
        }

         public class DoubleDispatchSampleTest{
            
            [Fact]
            public void ConnectTest(){
                
                DataShare share;

                var fileShare = new FileShare();
                var networkShare = new NetworkShare();

                share = fileShare;
                Assert.Equal("Connected to File Share", share.Connect());

                share = networkShare;
                Assert.Equal("Connected to Network Share", share.Connect());
            }
        }
    }
```

As can be seen, the abstract `Connect` method that is being called has different concrete implementations i.e. it is polymorphic in nature. Network and File Share classes provide their own implementations of this method. Appropriate implementation is called by the run time depending on which instance the method is being invoked on. This mechanism is known as Double or Multiple Dispatching.