# 19. Remove Nth Node From End of List
# Given the head of a linked list, remove the nth node from the end of the list and return its head.
class Solution {
public:
    ListNode* removeNthFromEnd(ListNode* head, int n) {
        if(head==nullptr||n<1) return head;
        int length=0;
        ListNode* curr=head;
        while(curr!=NULL){
            length++;
            curr=curr->next;
        }
        if(n==length){ // nth from end where n = length means first node from beginning
            ListNode* temp=head;
            head=head->next;
            delete temp;
            return head;
        }
        int positionFromStart=length-n;
        curr=head;
        for(int i=0;i<positionFromStart-1&&curr!=NULL;i++){
            curr=curr->next;
        }
        if(curr->next==NULL) return head;
        ListNode* temp=curr->next;
        curr->next=curr->next->next;
        delete temp;
        return head;
    }
};
