# Default_Method_Override_Java 8


Two different default methods in two different interfaces . how to implement in java 8? give the example?

In Java 8, if a class implements two interfaces that have default methods with the same method signature, then you must override that method in the class to resolve the conflict.

Let’s see an example:

Example:

		interface InterfaceA {
			default void show() {
				System.out.println("InterfaceA show()");
			}
		}

		interface InterfaceB {
			default void show() {
				System.out.println("InterfaceB show()");
			}
		}

// Class implementing both interfaces

		public class MyClass implements InterfaceA, InterfaceB {

			// Mandatory to override show() because of conflict
			@Override
			public void show() {
				// You can choose which interface's method to call
				InterfaceA.super.show();  // calling InterfaceA's show()
				InterfaceB.super.show();  // calling InterfaceB's show()
				System.out.println("MyClass show()");
			}

			public static void main(String[] args) {
				MyClass obj = new MyClass();
				obj.show();
			}
		}
Output:

		InterfaceA show()
		InterfaceB show()
		MyClass show()
		
		
Key Points:

Conflict happens when two interfaces have the same default method.

You must override the conflicting method.

Inside the overriding method, you can call specific interface methods using:

			InterfaceName.super.methodName();

Would you also like me to show a real-world example where this happens (like two services having a log() method)? 🚀

two different methods (like void generateReports) in two different interfaces B & B . how to implement in java 8? give the example?

	👉 If two different interfaces (say, Interface A and Interface B) have different default methods (both named differently like generateReport() and generateSummary()),
	👉 How to implement them in a class in Java 8?

✅ Answer:

	If the methods are different (different names) — no conflict happens!
	You can simply inherit them without needing to override anything (unless you want to customize).

Example:

			interface A {
				default void generateReport() {
					System.out.println("Generating report from Interface A");
				}
			}

			interface B {
				default void generateSummary() {
					System.out.println("Generating summary from Interface B");
				}
			}

			// Class implementing both interfaces
			public class MyClass implements A, B {

				// No conflict because method names are different
				// You can override if you want, but not necessary

				public static void main(String[] args) {
					MyClass obj = new MyClass();
					obj.generateReport();   // from Interface A
					obj.generateSummary();  // from Interface B
				}
			}
Output:

			Generating report from Interface A
			Generating summary from Interface B
			➡️ Important points:
			Since method names are different, Java knows which method belongs to which interface.

			No need to override unless you want custom behavior.

			You can use default implementations directly from the interfaces.

			Would you also like me to show an example where both methods have same signature but still no conflict by explicitly overriding? (optional but a cool trick!) 🚀


No..interface A{ having void show(), and interface B also having void show()...here while implementing in MyClass implements A, B  how to call this show()  method?

			✅ Both Interface A and Interface B have void show() method (same signature).
			✅ Now MyClass implements A, B.
			✅ How to implement and call the correct show() method?

			👉 Since both interfaces have the same method signature (show()), there is a conflict.
			👉 You MUST override show() in MyClass to resolve the conflict.
			👉 Inside, you can call A.super.show() or B.super.show() to access specific interface's default method.

Full Example:

			interface A {
				default void show() {
					System.out.println("Showing from Interface A");
				}
			}

			interface B {
				default void show() {
					System.out.println("Showing from Interface B");
				}
			}

			public class MyClass implements A, B {

				@Override
				public void show() {
					// Resolve conflict by choosing which default method to call
					A.super.show();  // Call Interface A's show()
					B.super.show();  // Call Interface B's show()
					System.out.println("Showing from MyClass");
				}

				public static void main(String[] args) {
					MyClass obj = new MyClass();
					obj.show();
				}
			}
Output:

			Showing from Interface A
			Showing from Interface B
			Showing from MyClass
			
			
✨ Important Rules:

			You must override the show() method because of conflict.

			Inside the overridden method:

			You can call A.super.show(); — to run Interface A’s method.

			You can call B.super.show(); — to run Interface B’s method.

			You can also write your own custom logic in MyClass.

Would you like me to also show how only one interface's show() can be called if you don't want both? (shortcut version!) 🚀


Now it's very clear:

			✅ Interface A and Interface B both have an abstract method void show(); (NOT default, no body).
			✅ You have a class MyClass implements A, B.

👉 In this case, there is no conflict.
👉 You just need to implement show() once in MyClass, because both interfaces only declare the method (no body).

Here's the example:

		interface A {
			void show();  // abstract method
		}

		interface B {
			void show();  // abstract method
		}

// Implementing class

		public class MyClass implements A, B {

			@Override
			public void show() {
				System.out.println("Implemented show() in MyClass");
			}

			public static void main(String[] args) {
				MyClass obj = new MyClass();
				obj.show();
			}
		}
Output:

Implemented show() in MyClass

✨ Important points:

    Only one implementation of show() is needed in MyClass.
    
    No need to mention A.super or B.super because there is no default method, only abstract method signatures.

Java is fine because both interfaces agree that a show() method must exist.










