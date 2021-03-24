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

## 多邊形的程式
```C
   glBegin(GL_POLYGON);

        glColor3f(0.2f, 0.4f, 0.0f);
       for (float angle=0; angle<3.1459265358979*2; angle+=0.01){
            glVertex2f(0.5*cos(angle),0.5*sin(angle));
       }

    glEnd();
```
## 考試重點

```C
{
　glBegin(GL_TRIANGLES);

        glColor3f(1.0f, 0.0f, 0.0f);   glVertex2f(0.0f,   1.0f);
        glColor3f(0.0f, 1.0f, 0.0f);   glVertex2f(0.87f,  -0.5f);
        glColor3f(0.0f, 0.0f, 1.0f);   glVertex2f(-0.87f, -0.5f);

    glEnd();
}
```

## 點滑鼠出現座標的程式
```C
#include <GL/glut.h>
#include <stdio.h>
void display()
{
    glClear(GL_COLOR_BUFFER_BIT | GL_DEPTH_BUFFER_BIT);
    glutSolidTeapot(0.3);
    glutSwapBuffers();
}
void mouse( int button, int  state, int x, int y)
{
    printf("button:%d state:%d x:%d y:%d\n", button, state, x, y);
}
int main(int argc, char**argv)
{
    glutInit( &argc, argv);
    glutInitDisplayMode(GLUT_DOUBLE | GLUT_DEPTH);
    glutCreateWindow("08163105");


    glutDisplayFunc( display);
    glutMouseFunc(mouse);

    glutMainLoop();
}
```

## 點滑鼠連線的程式

```C
#include <GL/glut.h>
int N=0, vx[3000], vy[3000];
void display()
{
    glClear(GL_COLOR_BUFFER_BIT | GL_DEPTH_BUFFER_BIT);
    glBegin(GL_LINE_LOOP);
    for(int i=0; i<N; i++){
        glVertex2f( (vx[i]-150)/150.0, -(vy[i]-150)/150.0);
    }
    glEnd();
    glutSwapBuffers();
}
void motion (int x, int y)
{
    vx[N]=x; vy[N]=y;
    N++;
    display();
}
int main(int argc, char**argv)
{
    glutInit( &argc, argv);
    glutInitDisplayMode(GLUT_DOUBLE | GLUT_DEPTH);
    glutCreateWindow("08163105");


    glutDisplayFunc( display);
    glutMotionFunc(motion);
    glutMainLoop();
}
```

## 旋轉圖示的程式
```C
#include <GL/glut.h>
int N=0, vx[3000], vy[3000];
float angle=0;
void display()
{
    glClear(GL_COLOR_BUFFER_BIT | GL_DEPTH_BUFFER_BIT);

    glPushMatrix();
    glRotatef(angle, 0, 0, 1);
    glBegin(GL_LINE_LOOP);
    for(int i=0; i<N; i++){
        glVertex2f( (vx[i]-150)/150.0, -(vy[i]-150)/150.0);
    }
    glEnd();
    glPopMatrix();
    glutSwapBuffers();
}
void keyboard ( unsigned char key, int x, int y)
{
    angle++;
    display();
}
void motion (int x, int y)
{
    vx[N]=x; vy[N]=y;
    N++;
    display();
}
int main(int argc, char**argv)
{
    glutInit( &argc, argv);
    glutInitDisplayMode(GLUT_DOUBLE | GLUT_DEPTH);
    glutCreateWindow("08163105");


    glutDisplayFunc( display);
    glutKeyboardFunc( keyboard);
    glutMotionFunc(motion);
    glutMainLoop();
}
```
