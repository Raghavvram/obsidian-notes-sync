```java
class Cuboid {
    private int length;
    private int breadth;
    private int height;

    private Cuboid(Builder builder) {
        this.length = builder.length;
        this.breadth = builder.breadth;
        this.height = builder.height;
    }

    public void show() {
        System.out.println("Cuboid dimensions: Length = " + length +
        ", Breadth = " + breadth + ", Height = " + height);
    }

    public static Builder getBuilder() {
        return new Builder();
    }

    public static class Builder {
        private int length;
        private int breadth;
        private int height;

        public Builder setLength(int length) {
            this.length = length;
            return this;
        }

        public Builder setBreadth(int breadth) {
            this.breadth = breadth;
            return this;
        }

        public Builder setHeight(int height) {
            this.height = height;
            return this;
        }

        public Cuboid build() {
            // You can add validation here if needed
            return new Cuboid(this);
        }
    }
}

public class Main {
    public static void main(String[] args) {
        Cuboid cuboid = Cuboid.getBuilder()
                               .setLength(10)
                               .setBreadth(5)
                               .setHeight(3)
                               .build();
        cuboid.show();
    }
}
```