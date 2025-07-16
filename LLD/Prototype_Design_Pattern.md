```java
class Cuboid implements Cloneable {
    private int length;
    private int breadth;
    private int height;

    public Cuboid() {
        // Default constructor
    }

    public Cuboid(int length, int breadth, int height) {
        this.length = length;
        this.breadth = breadth;
        this.height = height;
    }

    @Override
    public Cuboid clone() {
        try {
            return (Cuboid) super.clone(); // Shallow copy, sufficient for primitives
        } catch (CloneNotSupportedException e) {
            // This should not happen because we implement Cloneable
            throw new AssertionError();
        }
    }

    public void show() {
        System.out.println("Cuboid dimensions: Length = " + length +
                           ", Breadth = " + breadth +
                           ", Height = " + height);
    }

    public static void main(String[] args) {
        Cuboid original = new Cuboid(10, 5, 3);
        Cuboid copy = original.clone();

        original.show();
        copy.show();
    }
}
```