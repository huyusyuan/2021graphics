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

## 彩色茶壺的程式

```C
include <GL/glut.h>

static void display(void)
{
    glClear(GL_COLOR_BUFFER_BIT | GL_DEPTH_BUFFER_BIT);
    glBegin(GL_TRIANGLES);

    glColor3f(1.0f, 0.0f, 0.0f);   glVertex2f(0.0f,   1.0f);
    glColor3f(0.0f, 1.0f, 0.0f);   glVertex2f(0.87f,  -0.5f);
    glColor3f(0.0f, 0.0f, 1.0f);   glVertex2f(-0.87f, -0.5f);

    glEnd();
    glColor3f(1, 0, 0);

    glutSolidTeapot(0.3);
    glutSwapBuffers();
}

int main(int argc, char *argv[])
{
    glutInit(&argc, argv);
    glutInitDisplayMode(GLUT_RGB | GLUT_DOUBLE | GLUT_DEPTH);
    glutCreateWindow("08163105");
    glutDisplayFunc(display);
    glutMainLoop();
}
```

## 橢圓的程式
```C
#include <GL/glut.h>
#include <math.h>
void display()
{
    glClear(GL_COLOR_BUFFER_BIT | GL_DEPTH_BUFFER_BIT);
    glColor3d(1,0,0);
    glBegin(GL_POLYGON);
    for( int i=0; i<30; i++){
        float a = 3.1415926 * 2 / 30 *i;
        glVertex2f( 0.5+0.1*cos(a) ,0.2*sin(a) );
    }
    glEnd();
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
