# LeiBBLibrary

// Tree.hpp 文件
#ifndef Tree_hpp
#define Tree_hpp
#include <stdio.h>

class Tree {
publish:
  Tree(int size, int *pRoot);
  ~Tree();
  
  int *searchNode(int nodeIndex);
  bool AddNode(int nodeIndex,int direction, int *pNode);
  bool DeleteNode(int nodeIndex, int Pnode);
  void TreeTraverse();
  
protected:

private:
  int *m_pTree;
  int m_iSize;
}

----------------------------------------------------------------------------
//Tree.cpp 文件
#include "Tree.hpp"
#include <iostream>

using namespace std;

Tree::Tree(int size, int *pRoot)// 构造函数
{
    m_iSize = size;                 // 数组的容量
    m_pTree = new int[size];        //从堆中分配size大小的内存
    for (int i = 0; i < size; i++) {// 初始化为0
        m_pTree[i] = 0;
    }
    m_pTree[0] = *pRoot;//
}

//销毁树
Tree::~Tree()       //析构函数，销毁树
{
    delete []m_pTree;
    m_pTree = NULL;
}

//根据树的节点下标索引搜索节点
int *Tree::searchNode(int nodeIndex)
{
    if (nodeIndex < 0 || nodeIndex > m_iSize) {
        return NULL;
    }
    if (m_pTree[nodeIndex] == 0) {
        return NULL;
    }
    
    return &m_pTree[nodeIndex];
}

bool Tree::AddNode(int nodeIndex, int direction, int *pNode){
    if (nodeIndex < 0 || nodeIndex > m_iSize) {
        return NULL;
    }
    if (m_pTree[nodeIndex] == 0) {
        
        return NULL;
    }
    cout<<m_pTree[nodeIndex]<<endl;
    
    if (direction == 0) {
        if (nodeIndex * 2 + 1 > m_iSize) {
            return NULL;
        }
        
        if (m_pTree[nodeIndex * 2 + 1] != 0) {
            return NULL;
        }
        
        m_pTree[nodeIndex * 2 + 1] = *pNode;
    }
    if (direction == 1) {
        if (nodeIndex * 2 + 2 > m_iSize) {
            return NULL;
        }
        if (m_pTree[nodeIndex * 2 + 2] != 0) {
            return NULL;
        }
        m_pTree[nodeIndex * 2 + 2] = *pNode;
    }
    
    
    return true;
}

void Tree::TreeTraverse()
{
    for (int i = 0; i < m_iSize; i++) {
        cout<<m_pTree[i]<<" ";
    }
    
}

bool Tree::DeleteNode(int nodeIndex, int pNode)
{
    if (nodeIndex < 0 || nodeIndex > m_iSize) {
        return NULL;
    }
    if (m_pTree[nodeIndex] == 0) {
        return NULL;
    }
    
    m_pTree[nodeIndex] = 0;
    return true;
}
