# 2021graphics

## 圓的程式
```C
#include <GL/glut.h>
void display()
{
    glClear(GL_COLOR_BUFFER_BIT | GL_DEPTH_BUFFER_BIT);
    glColor3d(1,0,0);
    glutSolidSphere(0.5,30,30);
    glutSwapBuffers();
}
int main(int argc, char**argv)
{
    glutInit( &argc, argv);
    glutInitDisplayMode(GLUT_DOUBLE | GLUT_DEPTH);
    glutCreateWindow("Week03-circle");


    glutDisplayFunc( display);

    glutMainLoop();
}
```
