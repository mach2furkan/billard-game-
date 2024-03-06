

     // billard game for which designed by  furkan askin 
        #include <iostream>

        class Ball {
      private:
    double x, y; // Position of the ball
    double vx, vy; // Velocity components

        public:
    Ball(double posX, double posY, double velX, double velY) : x(posX), y(posY), vx(velX), vy(velY) {}

    void move(double dt) {
        x += vx * dt;
        y += vy * dt;
    }

    void collideWithWall(double width, double height) {
        if (x <= 0 || x >= width) {
            vx = -vx; // Reverse direction on collision with left or right wall
        }
        if (y <= 0 || y >= height) {
            vy = -vy; // Reverse direction on collision with top or bottom wall
        }
    }

    double getX() const {
        return x;
    }

    double getY() const {
        return y;
    }

    double getVX() const {
        return vx;
    }

    double getVY() const {
        return vy;
    }
      };

        int main() {
    const double dt = 0.1; // Time step for simulation
    const double tableWidth = 10.0; // Width of the table
    const double tableHeight = 5.0; // Height of the table

    Ball ball(1.0, 1.0, 1.0, 0.5); // Initialize ball position and velocity

    // Simulate for a few time steps
    for (int i = 0; i < 100; ++i) {
        ball.move(dt);
        ball.collideWithWall(tableWidth, tableHeight);

        // Print ball position
        std::cout << "Ball Position: (" << ball.getX() << ", " << ball.getY() << ")" << std::endl;
    }

    return 0;
      }
